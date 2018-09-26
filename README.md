tssc
====

multicast streaming desktop

Pythonで書いています。
クライアント・サーバともにVLCが必要となりますので別途インストールして下さい。

動作検証は、ubuntu14.04 LTSにて行っております。

#クライアント側のVLCコマンド

1.通常　vlc udp://@239.255.0.1 --network-caching=0 --udp-caching=0 --rtp-caching=0 --video-on-top --video-filter=magnify --width=400 --height=300 --no-qt-privacy-ask --no-ignore-config --qt-minimal-view

2.全画面　vlc udp://@239.255.0.1 --network-caching=0 --udp-caching=0 --rtp-caching=0 --fullscreen --no-qt-privacy-ask --no-ignore-config --qt-minimal-view

3.半画面　vlc udp://@239.255.0.1 --network-caching=0 --udp-caching=0 --rtp-caching=0 --width=200 --height=400 --no-qt-privacy-ask --no-ignore-config --qt-minimal-view

#サーバー側のVLCコマンド

1.通常・全画面　cvlc screen:// :screen-fps=20 :screen-caching=3000 :udp-caching=3000 :live-caching=300 --quiet --sout #transcode{vcodec=mp2v,vb=1024}:std{access=udp,mux=ts,dst=239.255.0.1,port=5004,udp-caching=0,rtp-caching=0,mux-caching=0

2.半画面　cvlc screen:// :screen-fps=20 :screen-caching=3000 :udp-caching=3000 :live-caching=300 --quiet --sout #transcode{vcodec=mp2v,vb=1024}:std{access=udp,mux=ts,dst=239.255.0.1,port=5004,udp-caching=0,rtp-caching=0,mux-caching=0}']