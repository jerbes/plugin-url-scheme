# Url Scheme plugin for Phonegap #
* By James Erbes
* For Cordova 3.0

# BASH script form adding handleOpenURL call to Android 
sed -i .bak 's/package com.starstar.me;/\
package com.starstar.me;\
import android.content.Intent;/g' platforms/android/src/com/myapp/me/MyApp.java

sed -i .bak 's/@Override/@Override\
  public void onStart() {\
      super\.onStart();\
      final Intent intent = getIntent();\
      String url = intent\.getDataString();\
      if(url != "" \&\& url != null) {\
          super\.sendJavascript("setTimeout(function() { handleOpenURL('\''" + url + "'\''); },1);");\
      }\
  }\
  @Override\
  protected void onNewIntent(Intent intent) {\
       super.onNewIntent(intent); setIntent(intent);\
  }\
  @Override/g' platforms/android/src/com/myapp/me/MyApp.java