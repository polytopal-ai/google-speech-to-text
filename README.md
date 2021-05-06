This script is for extracting and transcribing audio files from .mp4 video files into .srt formatted text files for subtitling purposes using Googles Speech-to-Text and Google Cloud Storage APIs. It outputs both a raw text transcription and a .srt formatted version. In the current version, this script requires you to authenticate your Google credentials through the gcloud CLI and also requires that you have ffmpeg installed locally on your machine (for video to audio conversion and compression)

## Polytopal Use Instructions for macOS

Make sure to have homebrew installed [from their instructions](http://brew.sh)

Make sure to install the following things:
```bash
brew install ffmpeg
pip install mkvenv
mkvenv
```

You should see an option to install the requirements from  `requirements.txt`. Go ahead and do that. If you don't see that option, just run:

```bash
pip install -r requirements.txt
```

Then go ahead and download your json certificate (ask Abhay) to your root of the directory.

Place your `.mp4` files into the `Interviews` folder for processing.

Then, execute the command to start the transcription:

```bash
python autorun.py Interviews/
```

The transcription should start up. It takes a while, around 30s per 1m of video, so for a 1 hour video it would take 30 minutes to transcribe. You can use a tool like [Amphetamine](https://apps.apple.com/us/app/amphetamine/id937984704?mt=12) to keep your computer from sleeping while it works.

## Old Instructions
Instructions for use

Use the Cloud Platform Console to create a new Cloud
Platform project, create an App Engine application, and
enable billing: https://console.cloud.google.com/
(Skip if project already set up)

Enable the Google Speech to Text API
in APIs and Services in new project dashboard

Set up a storage bucket in Google Cloud Storage


Download, install and set up Google SDK
https://cloud.google.com/sdk/
(authenticate your machine by following the auth instructions)

Install ffmpeg
    sudo apt update
    sudo apt install ffmpeg

Set your virtual environment

If you don't have virtualenv, install it using pip.

    sudo pip install virtualenv

Create an isolated Python environment, and install dependencies:

virtualenv env
source env/bin/activate
pip install -r requirements.txt

In goog.py change the bucket_name variable to the name of the storage bucket you wish to use

To run transcription script add .mp4 files to a specified directory

Then run:

    python autorun.py /path/to/directory/

The script will automatically strip the audio files from the video and convert them to .ogg format

The it uploads the audio to the gcloud storage bucket and
then passes its gcs_uri to the speech to text API for processing

When finished, it outputs both the .srt formatted file and raw text file into the specified directory

Note that if the program errors, it terminates as to not potentially abuse any API quota limits