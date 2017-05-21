
I compiled the included libs (libcrypto and libssl) from the original OpenSSL 1.0.2k (26 Jan 2017) source code.

The source code can be downloaded from the following site: https://www.openssl.org/source/

Some compiling instructions can be found here: https://wiki.openssl.org/index.php/Android

I used Ubuntu 16.04.2 as host system and arm-linux-androideabi as target.

The libcrypto.so and libssl.so can be included in a Qt-project in QtCreator as follows:
	1. select an android build kit
	2. open the "Projects"-tab
	3. add the .so files in the Android APK section as additional libraries.
		The QtCreator adds the files to the Qt project file (.pro) and places them in the right directories.
		If you would like to view the version your app uses, add the following lines to your main.cpp:
		
			// open ssl
			qDebug() << "SSL version at compile-time: " << QSslSocket::sslLibraryBuildVersionString();
			qDebug() << "SSL version at run-time: " << QSslSocket::sslLibraryVersionString();
			qDebug() << QCoreApplication::libraryPaths();
			
		The output for compile-time will be something like 1.0.0a and for run-time 1.0.2k as intended.
		The Google Play Store accepts apps with this version of openssl.
