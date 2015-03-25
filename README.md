# pdfview

<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context="${relativePackage}.${activityClass}" >

    <com.joanzapata.pdfview.PDFView
        android:id="@+id/pdfView"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />
	<TextView 
	    android:id="@+id/tv"
	    android:text="3/5"
	    android:layout_width="100dp"
	    android:layout_height="50dp"
	    android:layout_gravity="center_horizontal"
	    android:layout_marginTop="20dp"
	    />
</FrameLayout>


public class MainActivity extends Activity {
	
	WebView webView;
	
	PDFView pdfView;
	TextView tv;

	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main);
		tv = (TextView) findViewById(R.id.tv);
		pdfView = (PDFView) findViewById(R.id.pdfView);
		
				pdfView.fromAsset("zmt.pdf")
				.onPageChange(new OnPageChangeListener() {
					
					@Override
					public void onPageChanged(int page, int pageCount) {
						// TODO Auto-generated method stub
						tv.setText(""+page+"/"+pageCount);
					}
				})
			    .pages(null)
			    .defaultPage(1)
			    .showMinimap(true)
			    .enableSwipe(true)
			    .load();
			}
