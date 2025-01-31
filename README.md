# Krux File Signer (aka __ksigner__)

Is a python script to help make airgapped signatures with Krux devices.
It also can verify the signatures.
There's also a GUI version in development

## Development

### Fetching the code

```bash
git clone https://github.com/selfcustody/krux-file-signer.git
```

### Install dev tools

The `ksigner` code is a Python script
that should be installed with Poetry. To generate
a new `poetry.lock` file use: `poetry lock --no-update`.

With `pip`, you can do:

```bash
pip install poetry
poetry install
```

This will also install all development tools so that you can run pylint,
format code with black, and build an agnostic OS executable. 

### Format code

```bash
poetry run black ./src
```

### Lint code

```bash
poetry run pylint ./src
```

### Build executable

```bash
poetry run pyinstaller ./src/ksigner.py
```

The generated executable will be placed on 
`dist/ksigner/ksigner`


### Run the GUI version

```bash
poetry run python src/ksignerGUI.py
```

### Build the GUI version executable

```bash
poetry run pyinstaller ./src/ksignerGUI.py
```

The generated executable will be placed on 
`dist/ksignerGUI/ksignerGUI`


## Usage

### Commands

#### Help

Running `./dist/ksigner/ksigner --help` will show:

```bash
usage: ksigner [-h] {sign,verify} ...

This python script is a tool to create air-gapped signatures of files using Krux. The script can also convert hex
publics exported from Krux to PEM public keys so signatures can be verified using openssl.

positional arguments:
  {sign,verify}  sub-command help
    sign         sign a file
    verify       verify signature

options:
  -h, --help     show this help message and exit
```

#### sign

Running `./dist/ksigner/ksigner sign --help`, will show:

```bash
usage: ksigner sign [-h] [-f FILE_TO_SIGN] [-o FILE_OWNER] [-u] [-l]

options:
  -h, --help            show this help message and exit
  -f FILE_TO_SIGN, --file FILE_TO_SIGN
                        path to file to sign
  -o FILE_OWNER, --owner FILE_OWNER
                        the owner's name of public key certificate, i.e, the .pem file (default: 'pubkey')
  -u, --uncompressed    flag to create a uncompreesed public key (default: False)
  -l, --verbose-log     verbose output (default: False)

```

#### verify

Running `/dist/krux-file-signer/krux-file-signer verify --help`, will show:

```bash
usage: ksigner verify [-h] [-f VERIFY_FILE] [-s SIG_FILE] [-p PUB_FILE]

options:
  -h, --help            show this help message and exit
  -f VERIFY_FILE, --file VERIFY_FILE
                        path to file to verify
  -s SIG_FILE, --sig-file SIG_FILE
                        path to signature file
  -p PUB_FILE, --pub-file PUB_FILE
                        path to pubkey file
```

