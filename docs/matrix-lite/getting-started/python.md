<h2 style="padding-top:0">Prerequisite MATRIX HAL</h2>

<!-- MATRIX HAL is at the base of each MATRIX Lite library. This makes it a requirement to have it installed on your Raspberry Pi. Below are the installation instructions -->

> Make sure you have installed [MATRIX HAL](/matrix-hal/getting-started/), before continuing.

## Python Setup

Install Python 3
```language-bash
sudo apt-get install python3-pip
```

Create A Project Folder.
```language-bash
mkdir lite_py
cd lite_py
touch app.py
```

Download the matrix-lite-py Package. Note, the module is called `matrix_lite`.
```language-bash
pip3 install matrix-lite
```

<br/>
## Next Steps
With your device now setup, you can visit our [Reference](../py-reference) page to get started with MATRIX Lite.