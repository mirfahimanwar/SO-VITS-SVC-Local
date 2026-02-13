# SO-VITS-SVC-Local
This is for those who have a higher end GPU and wish to run SO-VITS-SVC locally instead. You could technically run a backend url via Google Collab, but I found that to a pain.

Create a virtual environment:
python -m venv venv

Activate the virtual environment:
/venv/Scripts/activate

Install the following:
python -m pip install -U pip wheel
pip install -U so-vits-svc-fork

Make sure the file structure is as follows:
D:\SO-VITS-SVC\
    ├── models\
    │   └── YourModelName\
    │       ├── G_xxxxx.pth
    │       ├── config.json
    │       └── kmeans_model.pt (optional)
    ├── input\
    │   └── your_audio.wav
    └── output\

Run Inference:
Note: Make sure there are no spaces or special characters in the filenames
svc infer input\your_audio.wav -m models\YourModelName\G_xxxxx.pth -c models\YourModelName\config.json -t 0 --f0-method crepe -o output\converted.wav

I.E: svc infer input\noroadsleft.mp3 -m models\ChesterBennington\G_79200.pth -c models\ChesterBennington\config.json -t 0 --f0-method crepe -o output\converted.wav

Or, if the quality doesn't seem that good, you can try: 
# Add the no-auto-predict flag and adjust other parameters (this is what the Google Colab version uses
svc infer input\noroadsleft.mp3 -m models\ChesterBennington\G_79200.pth -c models\ChesterBennington\config.json -t 0 --f0-method crepe -n 0.4 -o output\converted.wav --no-auto-predict-f0
