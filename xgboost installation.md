# XGBosst installation

Since I had this problem on MacOS, I wanted to save a practical guide that I found on the internet. I hope it helps you too.

## How to install XGBoost on Mac

This is the link to the original post: [StackOverflow](https://stackoverflow.com/questions/57483499/how-to-install-xgboost-on-macos)

### Step 1: Python virtual evnironment should be installed

First, you need to make sure that you have python installed on your machine.
You can do so by useing homebrew: (if you don't know what it is you can check it out [here](https://brew.sh/))

```bash
brew install python
```

Then, you need to install Python virtual environment. You can install it by running the following command in your terminal:

```bash
pip install virtualenv
pip venv .venv
source .venv/bin/activate
```

This will create the virtual environment and activate it for you.

After that you can install the required packages.
use the requirements.txt file from this repository to install the required packages.

```bash
pip install -r requirements.txt
```

You may get an error like this:

```text
ERROR: Could not find a version that satisfies the requirement xgboost (from versions: none)
ERROR: No matching distribution found for xgboost
```

then you have to install XGBoost manually.

### Step 2: Install XGBoost

In macOS, you have to have a c compiler installed. You can install it by running the following command in your terminal:

```bash
xcode-select --install
gcc --version
# to see if the c compiler is installed
```

Then, you need to install the libomp library. (this is a requirement for MacOS)

You can install it by running the following command in your terminal:

```bash
brew install libomp
```

After that, you have to go into the project directory and install XGBoost manually.

First you need to aquire the source code of XGBoost.
You can do so by running the following command in your terminal:

```bash
git clone --recursive https://github.com/dmlc/xgboost
```

It is important to use the `--recursive` flag to clone the repository.

Then, you need to go into the cloned directory and install XGBoost.

```bash
cd xgboost
mkdir build
cd build
cmake ..
make -j$(nproc)
```

to use nproc (number of processors) you can run the following command:

```bash
brew install coreutils
```

After that, you need to install the python package.

-> Remember you have to be inside the virtual environment to install the package.
Other wise it will install XGBoost globally.

```bash
source .venv/bin/activate
```

You can install the python package by running the following command in your terminal:

```bash
cd ../python-package
pip install -e .
```

This will install the XGBoost package from the source code.
