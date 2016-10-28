package com.example.asyncprogress;

import java.util.Random;

import android.app.Activity;
import android.opengl.Visibility;
import android.os.AsyncTask;
import android.os.Bundle;
import android.os.SystemClock;
import android.view.Menu;
import android.view.MenuItem;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.ProgressBar;

public class MainActivity extends Activity {
	ProgressBar pb1;

	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main);

		Button btn1 = (Button) findViewById(R.id.btn1);

		btn1.setOnClickListener(new OnClickListener() {

			@Override
			public void onClick(View v) {
				
			AsyncTask<Void, Integer, Void> task = new AsyncTask<Void, Integer, Void>() {
				
				@Override
				protected void onPreExecute() {
					// TODO Auto-generated method stub
					super.onPreExecute();
					pb1 = (ProgressBar) findViewById(R.id.pb1);
					pb1.setMax(100);
					pb1.setVisibility(View.VISIBLE);
					
				}
				
				@Override
				protected Void doInBackground(Void... params) {
					for(int i =0; i < 100; i++)
					{
						publishProgress(i);
						try {
							Thread.sleep(new Random().nextInt(250) + 25);
						} catch (InterruptedException e) {
							// TODO Auto-generated catch block
							e.printStackTrace();
						}
					}

					
					return null;
				}
				
				 @Override
				    protected void onProgressUpdate(Integer... values) {
				        super.onProgressUpdate(values);

				        pb1.setProgress(values[0]);
				        //txtprogrss.setText("progress update"+ values[0]+"%");

				    }
				 
				 @Override
					protected void onPostExecute(Void result) {
						// TODO Auto-generated method stub
						super.onPostExecute(result);
						pb1.setVisibility(View.INVISIBLE);
					}
				
			};
				//task.execute();
				task.executeOnExecutor(AsyncTask.THREAD_POOL_EXECUTOR);
			}// end onclick 
		});

	}

	@Override
	public boolean onCreateOptionsMenu(Menu menu) {
		// Inflate the menu; this adds items to the action bar if it is present.
		getMenuInflater().inflate(R.menu.main, menu);
		return true;
	}

	@Override
	public boolean onOptionsItemSelected(MenuItem item) {
		// Handle action bar item clicks here. The action bar will
		// automatically handle clicks on the Home/Up button, so long
		// as you specify a parent activity in AndroidManifest.xml.
		int id = item.getItemId();
		if (id == R.id.action_settings) {
			return true;
		}
		return super.onOptionsItemSelected(item);
	}
}
