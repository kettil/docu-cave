# RPi-Jukebox-RFID

- Update/upgrade the rpi

  ```bash
  sudo apt-get update
  sudo apt-get dist-upgrade
  ```

- Edit `/boot/config.txt`

  ```bash 
  # Enable audio (loads snd_bcm2835)
  #dtparam=audio=on
  dtoverlay=hifiberry-dac
  ```

- Edit `/etc/asound.conf`

  ```bash
  pcm.hifiberryMiniAmp {
      type softvol
      slave.pcm "plughw:0"
      control.name "Master"
      control.card 0
  }
  
  pcm.!default {
      type       plug
      slave.pcm  "hifiberryMiniAmp"
  }
  ```
  
- `sudo reboot`

- Call `aplay -l`

  ```bash
  card 0: sndrpihifiberry [snd_rpi_hifiberry_dac], device 0: HifiBerry DAC HiFi pcm5102a-hifi-0 []
  Sub-Device: 1/1
  Sub-Device #0: subdevice #0
  ```
  
- Call `speaker-test -D hifiberryMiniAmp -c 2` - There's a rush playing.

- Call `omxplayer -o alsa "<path to mp3 file>"`

- Edit `'/etc/mpd.conf`

  ```bash
  audio_output {
          type            "alsa"
          name            "My ALSA Device"
  #       device          "hw:0,0"        # optional
  #       mixer_type      "hardware"      # optional
  #       mixer_device    "default"       # optional
          mixer_control   "Master"        # optional
  #       mixer_index     "0"             # optional
  }
  ```


## Source:
- https://forum-raspberrypi.de/forum/thread/36628-hifiberry-miniamp-aktivieren/?postID=307345#post307345
- https://forum-raspberrypi.de/forum/thread/36628-hifiberry-miniamp-aktivieren/?postID=307662#post307662
- https://github.com/MiczFlor/RPi-Jukebox-RFID/issues/261#issuecomment-433740032
