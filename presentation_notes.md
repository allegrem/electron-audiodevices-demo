# Intro
https://aircall.io
aircall front end dev, travail sur qualité des appels (notamment gestion des périphériques audio)

https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices
https://github.com/allegrem/electron-audiodevices-demo/blob/ex01/index.html
uniquement des features web, rien d’exclusif à electron
mais “sélection des devices” intéressant pour se rapprocher d’une expérience desktop native : communication (ex skype, aircall,…) ; audio processing / musique 

# EX01
“default” => dépend de la préférence système
“built in” => micro/speakers intégré OU port jack (impossible de faire la différence au niveau de chrome)

“deviceId” => [https://w3c.github.io/mediacapture-main/#dom-mediadeviceinfo-deviceid] depends on page’s origin, persist across sessions as soon as a live stream is attached to a local device or permission to access local devices has been granted, reset when persistent storage is cleared
“groupId” => same if devices belongs to the same physical device ; not persisted across sessions

groupId peut permettre de savoir quel “default” device est sélectionné

# EX02
jusqu’à Chrome 56, derrière un flag (enable “Experimental Web Platform features” or “--enable-blink-features=OnDeviceChange”)
attention !! “device change” appelé quand la liste des devices change, mais pas quand les informations des device change (en particulier le groupId de “default”)

# EX03
(rien de particulier)

# EX04
aller directement au code à partir de “getUserMedia”

# EX05


# Problèmes connus (!! SI J'AI LE TEMPS !!)
Mac : problème (hardware?) avec les headsets en jack => introduit echo ~350ms et l’AEC a du mal à le corriger
Mac : deadlock dans la stack audio => freeze de l’audio input (il faut relancer le browser)
Nouvel AEC (chrome 59?) “AEC3” 
Sortie de veille pas toujours très bien gérée 

# Conclusion
intéressant à croiser avec d’autres technos: webrtc, webaudio, … 
Audio/Vidéo => encore assez expérimental, surtout si couplé avec d’autres technos récentes (webaudio, webrtc) ; parfois peu documenté ou beaucoup de features browser-specific (plutôt pour webrtc) ; “moving target”, fait partie des APIs qui évoluent beaucoup en ce moment (encore plus flagrant sur electron avec les bumps de plusieurs versions de chrome)
RTFM ;)
