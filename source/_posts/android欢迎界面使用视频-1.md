---
title: android欢迎界面使用视频
date: 2017-05-15 21:48:15
tags:
---



在WelcomeActivity.class中
    
		videoview = (MyVideoView) findViewById(R.id.videoview);
    	videoview.setVideoURI(Uri.parse("android.resource://"+this.getPackageName()+"/"+R.raw.video));
    	videoview.start();
      	videoview.setOnCompletionListener(new MediaPlayer.OnCompletionListener() {
            @Override
          	  public void onCompletion(MediaPlayer mediaPlayer) {
                videoview.start();
            }
   		});

video保存在res/raw目录下，布局的时候在这个视频上一般都有个Button，“立即体验”或“开始使用”之类的，点击该button应该跳转到下一个activity并finish当前activity


		button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if(videoview.isPlaying()){
                    videoview.stopPlayback();
                    videoview=null;
                }
                //此处应该跳转到MainActivity
                WelcomeActivity.this.finish();
            }
        });
        

全屏播放视频要重新定义VideoView

		public class MyVideoView extends VideoView {
    		public MyVideoView(Context context) {
        		super(context);
		    }
		    public MyVideoView(Context context, AttributeSet attrs) {
		        super(context, attrs);
		    }
		    public MyVideoView(Context context, AttributeSet attrs, int defStyle) {
		        super(context, attrs, defStyle);
		    }
		    @Override
		    protected void onMeasure(int widthMeasureSpec, int heightMeasureSpec) {
		        int width = getDefaultSize(0, widthMeasureSpec);
		        int height = getDefaultSize(0, heightMeasureSpec);
		        setMeasuredDimension(width, height);
		    }
		    @Override
		    public void setOnPreparedListener(MediaPlayer.OnPreparedListener l) {
		        super.setOnPreparedListener(l);
		    }
		    @Override
		    public boolean onKeyDown(int keyCode, KeyEvent event) {
		        return super.onKeyDown(keyCode, event);
		    }
		}

