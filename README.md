# VLCView
## 使用方法
### 1. 添加libvlc至libs文件夹
### 2. 在module中的build.grade 添加  
> implementation(name: 'libvlc-3.0.0-1.9.8', ext: 'aar')
### 3. 添加view到xml文件：
```
<VideoViewer
    android:id="@+id/surface"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    />
```
### 4. 在Java文件里面创建播放器：
_在onResume()里面添加：_
```
VideoViewer mSurfaceView = findViewById(R.id.surface);
mSurfaceView.post(new Runnable() {
	@Override
	public void run() {
		if (!sURL.startsWith("http")) {
			mSurfaceView.createPlayer(sURL, true, 100);
		}else{
			mSurfaceView.createPlayer(sURL, true, 10000);
		}
	}
});
```
_在OnPause()里面添加：_
```
if(mSurfaceView != null){
  mSurfaceView.releasePlayer()
}
```
OVER!!!!
