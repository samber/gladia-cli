# gladia-cli

## Python Based CLI

### Direct install
Linux
```
wget https://github.com/gladiaio/gladia-cli/raw/main/python/dist/linux_x64_gladia && \
mv linux_x64_gladia gladia && \
chmod +x gladia
```

MacOS ARM
```
wget https://github.com/gladiaio/gladia-cli/raw/main/python/dist/macos_arm64_gladia && \
mv macos_arm64_gladia gladia && \
chmod +x gladia
```

Windows
```
wget https://github.com/gladiaio/gladia-cli/raw/main/python/dist/gladia_cli.exe
```

### Build from source
```
$ pipenv shell
$ pip install -r requirements.txt
```

to build on Macos or Linux run
```
$ ./build.sh 
```
the resulting gladia_cli is in dist 


to build on windows run
```
.\build.bat
```
the resulting gladia_cli.exe is in dist 

## Go Based CLI (New, Faster but alpha)
### Direct install
Linux X64
```
wget https://github.com/gladiaio/gladia-cli/raw/main/go/dist/gladia-darwin-amd64
```

Linux X32
```
wget https://github.com/gladiaio/gladia-cli/raw/main/go/dist/gladia-linux-armv7
```

Linux ARM
```
wget https://github.com/gladiaio/gladia-cli/raw/main/go/dist/gladia-darwin-arm64
```

MacOS Intel
```
wget https://github.com/gladiaio/gladia-cli/raw/main/go/dist/gladia-darwin-amd64
```

MacOS ARM
```
wget https://github.com/gladiaio/gladia-cli/raw/main/go/dist/gladia-darwin-arm64
```

Windows
```
wget https://github.com/gladiaio/gladia-cli/raw/main/go/dist/gladia-windows-amd64.exe
```

### Build from source
```
$ cd go
$ ./compile.sh
```


## Usage
here is the usage:

```
$ ./gladia --help
Usage: gladia [OPTIONS]

  Transcribe an audio file or an audio url using the Gladia API.

Options:
  --audio-url TEXT                URL of the audio file to be transcribed.
  --audio-file TEXT               Path to the audio file to be transcribed.
  --language-behaviour TEXT       Determines how to handle multi-language
                                  audio.
  --language TEXT                 Language spoken in the audio file.
  --transcription-hint TEXT       Hint to the transcription model. You can
                                  pass names, topics, custom vocabulary, etc.
  --noise-reduction               Apply noise reduction to the audio.
  --diarization                   Perform speaker diarization.
  --diarization-max-speakers TEXT
                                  Determines the maximum number of speakers to
                                  be detected.
  --direct-translate              Activate direct translation to the specified
                                  language.
  --direct-translate-language TEXT
                                  Language to which to translate the
                                  transcription, need to activate the direct
                                  translation using --direct-translate.
  --text-emotion                  Activate text emotion recognition.
  --summarization                 Activate summarization.
  --output-format TEXT            Format in which to return the transcription
                                  results. Possible values: table, json, text,
                                  srt, vtt, plain.
  --gladia-key TEXT               API key for Gladia. Get it at
                                  https://app.gladia.io/account
  --save-gladia-key               Save the API key to a configuration file.
  --help                          Show this message and exit.
```

Authentication:
1. get you Gladia key here: https://app.gladia.io/account
2. save the key if needed using
```
$ ./gladia --gladia-key MY_GLADIA_KEY --save-gladia-key
```
3. or use it inline for each request
```
$ ./gladia --gladia-key MY_GLADIA_KEY --OTHER_OPTIONS ...
```


Basic Example:
```
$ ./gladia_cli --audio-url http://files.gladia.io/example/audio-transcription/split_infinity.wav

Transcribing audio file...
Transcript

 time_begin  time_end  probability  language  speaker        transcription
 0.09        2.07      0.49         en        not_activated  Split infinity
 2.13        5.19      0.65         en        not_activated  in a time when less is more
```

