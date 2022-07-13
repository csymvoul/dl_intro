{
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "VxmQ_lNGvZzf"
      },
      "source": [
        "# Machine Learning (ML)\n",
        "\n"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "jAhqU_kib9j7"
      },
      "source": [
        "## What is Machine Learning?\n",
        "* A subset of Artificial Intelligence that aims at giving the computer the ability to learn from data without being explicitly shown (programmed) how to do that.\n",
        "\n",
        "![ML_DL.png](Figures/ML_DL.png)\n",
        "\n",
        "A ML model is able to _gradually improve its performance_, by repeating a specific process, without being re-developed to do so.\n"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "yBNzRduycHWZ"
      },
      "source": [
        "## Purpose\n",
        "It's purpose is to create machines that are capable of: \n",
        "* learning, \n",
        "* improve their perfomance in specific areas,\n",
        "* via the use of earlier knowledge and experience.\n",
        "\n",
        "By experience we mean the __data__, the __measurements__ we may have, and the __observations__. "
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "lenuYiEhcMX7"
      },
      "source": [
        "## Machine Learning types\n",
        "* __Supervised learning__: A ML model is trained over data that have labels. Typical supervised learning problems regard: \n",
        "    - __Classification__: Classify input data to pre-defined classes. E.g.classify clothing into t-shirts, boots, shorts, etc.\n",
        "    - __Regression__: Identify a numerical relationship between the input and the output data. E.g., Predict the temperature of a city based on historical data, etc.\n",
        "* __Unsupervised learning__: A ML model aims at learning patterns from unlabeled data. Typical unsupervised learning problems regard: \n",
        "    - __Clustering__: A ML model needs to divide the input data into a number of groups (aka. clusters). E.g., group users based on their location \n",
        "* __Semi-supervised learning__: A hybrid problem, where a ML model needs to combine a small number of labeled data with a large number of unlabeled data. \n",
        "* __Re-inforcement learning__: An (intelligent) agent works its way around an environment and aims at maiximinz a cumulative reward. E.g., a self-driving car, or a chess playing agent.\n"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "g_F9rvGUcP_z"
      },
      "source": [
        "## Machine Learning algorithms\n",
        "For each problem, there exist several algorithms. For instance: \n",
        "* For __classification problems__, we may use a binary classifier two split the data into two classes, or a multi-class classifier if there exist several classes. Such algorithms include, Logistic Regression, Support Vector Machines, Decision Trees, Random Forests, etc.\n",
        "* For __clustering problems__, the algorithms include DBSCAN, K-Means, K-Medoids, Hierarchical clustering, etc."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "OHBq39Jgb0Y_"
      },
      "source": [
        "# Deep Learning (DL)\n",
        "It is a type of Machine Learning, based on Artificial Neural Networks, that imitates the way humans earn knowledge. It can be used for solving supervised, semi-supervised and unsupervised learning problems. \n",
        "\n",
        "![Deep_Learning_Network.png](Figures/deep_learning_network.png)\n",
        "\n",
        "A DL network is in fact, a large Neural Network, that consists of neurons that are interconnected through layers. There exist 3 categories of layers: \n",
        "1. the input layer where the input data are inserted in the networkm,\n",
        "2. the hidden layers, that are between the input and output layers, whose neurons receive inputs and produce outputs given an activation function(this is where the magic happens),\n",
        "3. the output layer, which is the final layer of a (Deep) Neural Network, where the predictions are obtained.\n",
        "\n",
        "There exist several types (aka architectures or classes) of DNN such as: \n",
        "- Convolutional Neural Networks (this is what we will use today)\n",
        "- Recurrent Neural Networks\n",
        "- Self-organizing Maps\n",
        "- Auto-encoders, etc."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "zN13a1jUeC-g"
      },
      "source": [
        "## Activation functions\n",
        "An activation function  transforms the input of a hidden layer into an output. This output is then forwarded to the next layer as input. \n",
        "\n",
        "![neuron_af.png](Figures/neuron.png)\n",
        "\n",
        "Where: \n",
        "- $x_i$ are the input data \n",
        "- $w_i$ the weight of each input \n",
        "- $β$ is the bias\n",
        "- $f$ is the activation function"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "ff2meSFEiVIX"
      },
      "source": [
        "## Convolutional Neural Networks\n",
        "Most commonly used for analyzing images. Such networks, work their way towards their prediction by gradually identifying features (from low level to higher level ones), as shown in the figure below:\n",
        "\n",
        "![cnn_features.png](Figures/cnn_features.png)\n",
        "\n",
        "\n"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "R-QsT5zImyQT"
      },
      "source": [
        "# Practical example\n",
        "So that is enough with the theoretical stuff. It's time to actually develop, train and validate our own DL model. \n",
        "\n",
        "What we will do today, is create a _CNN model_ that will be trained using the __[Fashion MNIST](https://www.kaggle.com/datasets/zalando-research/fashionmnist)__ data set, which consists of: \n",
        "- 60,000 examples for training, and  \n",
        "- 10,000 examples for testing \n",
        "\n",
        "Our goal is to train that model in order to successfully predict the class of an object in an image. The available classes are the following: \n",
        "- 0 T-shirt/top\n",
        "- 1 Trouser\n",
        "- 2 Pullover\n",
        "- 3 Dress\n",
        "- 4 Coat\n",
        "- 5 Sandal\n",
        "- 6 Shirt\n",
        "- 7 Sneaker\n",
        "- 8 Bag\n",
        "- 9 Ankle boot\n",
        "\n",
        "Each image is in grayscale and a dimension of 28x28 pixels, for a total of 784 pixels. Each pixel has an integer value in the range of [0,255]."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "7kiyTDpWonep"
      },
      "source": [
        "## Installing dependencies"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "dvwmp5uboyH_"
      },
      "source": [
        "**Note:** whenever a command starts with `!`, it is ran on the terminal of the VM."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "NgFbIwv_pIZD"
      },
      "source": []
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "Il_cxJ2Fmx-r"
      },
      "outputs": [],
      "source": [
        "!pip install tensorflow"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "bYk2dVTQpDKL"
      },
      "source": [
        "## Import TensorFlow and other helper libraries"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 1,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 35
        },
        "id": "rTwST_S2pBVM",
        "outputId": "24d4ab66-c685-405c-94a4-94fd5aff178c"
      },
      "outputs": [
        {
          "data": {
            "application/vnd.google.colaboratory.intrinsic+json": {
              "type": "string"
            },
            "text/plain": [
              "'2.8.2'"
            ]
          },
          "execution_count": 1,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "import tensorflow as tf\n",
        "import math\n",
        "import numpy as np\n",
        "import matplotlib.pyplot as plt\n",
        "\n",
        "# Verify that TensorFlow is properly imported, by checking the version\n",
        "tf.__version__"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "gMnfvEi-pQCH"
      },
      "source": [
        "## Import Fashion MNIST data set from the TensorFlow Data sets collection"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 2,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 299,
          "referenced_widgets": [
            "2df75c343163464390df367797b03287",
            "62a4796e16b74bfe9f83ae43b720a9df",
            "092db04522ff4fc59a1ddea2839ca336",
            "07af05b798054560a54d85730a5148be",
            "a6e1d2d13417402a94c13fbcfc4a38b3",
            "1c6b5940911a4f059c830053b68aa7bf",
            "b7de0805b33b4fffa35a68dbfc9fa07f",
            "6296cb36821745a5bd73776a7605940c",
            "318473cb3bdb47838493752e11184ee5",
            "17256531b0914552bf0758666d601645",
            "57ddcc781d764f439010508da5cc1d61",
            "cb78a473b6c34646bf30a201c7f5598e",
            "2eabbd90ae944a12affe7ac1baedea6b",
            "173b870dc7d34f649a2c94bcfcff72fc",
            "5524d6c3ebad4a7ebda398d43d8488b7",
            "408db07d4d984e6c887eefa633a72a2e",
            "6b5d3ef3a3c64f32b53fe2382c37b02b",
            "3860220eeda8448fb840c232f8bbc7d7",
            "96b8adde241e4ebb91107228e459de4c",
            "d1231e61faaa4619be6a234fd821037d",
            "88ba38d6890c4680a5af173738fa6003",
            "1a83e61052014ade94c318ef61884cea",
            "975cf3e668ea4ad99f3cf1fe35c44c81",
            "e969e53722dc4da996f2a057ab29422e",
            "3c06489d7c08415db37da297301e5691",
            "6af42b282e27419c8940a7cd2901117b",
            "269ae71402544d258b59f265c9352134",
            "6dc2952c05064b0dac0d50749e9ca163",
            "55209c0f729547bb843a0184db07b1cc",
            "375caaa2e2cf46ee84e069715e58526d",
            "154d490f83384f85a9ab454ffbf5743d",
            "5ba3be176838422a9d4a490d47fcbcdb",
            "0cd6b0ba936648038e2a7c1edf8c13bf",
            "9c71a40348394f9993b9a6afdb6d8ed7",
            "61d78a74b4f847b580911cb7054fb4d3",
            "fa030d8a56de418b9c27c00259898a10",
            "7d1d2609565d4c7388763c542ca5a2aa",
            "8ada5f761f214be887f207073ef28b5b",
            "2fcda1efbe9c4efe8675de75e629a21b",
            "2e22f492d30d4271a5c15819b3898a9f",
            "cc27b05b821445c7aa7e522c8e169b61",
            "a00d66d782a84ec48be6baee1647340f",
            "20f2fba8b7424d6099d4a15522061417",
            "6ed2836d940f40c58e930da6dcf3be46",
            "e9548d82467f471981626fdf90d5b84d",
            "5a8a389390924d6d81e0ac38cdc60ed6",
            "576dbf67ce624ab8b371d6491f999769",
            "6c7b9d968c024e7ab94499e852a72b02",
            "1965c84f87e14e1aabd14a4d0e859284",
            "b09f8a68397743dab901b9b6cfa44642",
            "66bc597581ab422cb4e302d88165e633",
            "488fa7647d024200bc6c9a78038b4fba",
            "75c7636a4b014a2f868942e4134dcbac",
            "77c7d6a33ec141e58bb2d4a93342d83d",
            "045ebc8d71cd4b409c9982bff55a9462",
            "bc2348dcbde2414bb99729662a3763f5",
            "4c541d150a2849339653b969e9d33abc",
            "c77fdab52ff24f41b2c2ea7f9619f1f7",
            "c77ac8dc74aa4b919227e8d94e97a48e",
            "94143fc52b7949e99511fdd34e0406dc",
            "5c10d39849464fd0bbd6e22be13ce254",
            "6deff8ebd6eb434d943f22e505ea3670",
            "bdb7dc2a1019442a94d80a2dd85f0a01",
            "f4e51270bf8f47f18591b5ede0cf22ce",
            "98365ff527ba429aafc5398b72382054",
            "d16c627c81064dd3b9a2d3291e703388",
            "972c505f816d4414913fbb73cd2436fb",
            "c46402005c874fae9c36bdef235a091a",
            "19a370bdb7c14cbba2d997fd21e6658e",
            "00af9da286054a2f9e2c33d13e2d1490",
            "93f0bba3a59f452c844c4e06314ebb9e",
            "8270ae33d035459ca42f9c59b8eaa3da",
            "e0db0a4020b6440486ecce82ffac32a3",
            "9cd14d5404b049dcbe535827d6e4a224",
            "74dc651dec6840cbac15ff24366221d4",
            "e717fabe52c648209ba8089ceb233f55",
            "ad63069f2f9f449b8cd772f0238bd3ba"
          ]
        },
        "id": "OaQmY8xdvTPi",
        "outputId": "b2eac204-35b7-43f3-f9d2-e5053e0d7282"
      },
      "outputs": [
        {
          "name": "stdout",
          "output_type": "stream",
          "text": [
            "\u001b[1mDownloading and preparing dataset fashion_mnist/3.0.1 (download: 29.45 MiB, generated: 36.42 MiB, total: 65.87 MiB) to /root/tensorflow_datasets/fashion_mnist/3.0.1...\u001b[0m\n"
          ]
        },
        {
          "data": {
            "application/vnd.jupyter.widget-view+json": {
              "model_id": "2df75c343163464390df367797b03287",
              "version_major": 2,
              "version_minor": 0
            },
            "text/plain": [
              "Dl Completed...: 0 url [00:00, ? url/s]"
            ]
          },
          "metadata": {},
          "output_type": "display_data"
        },
        {
          "data": {
            "application/vnd.jupyter.widget-view+json": {
              "model_id": "cb78a473b6c34646bf30a201c7f5598e",
              "version_major": 2,
              "version_minor": 0
            },
            "text/plain": [
              "Dl Size...: 0 MiB [00:00, ? MiB/s]"
            ]
          },
          "metadata": {},
          "output_type": "display_data"
        },
        {
          "data": {
            "application/vnd.jupyter.widget-view+json": {
              "model_id": "975cf3e668ea4ad99f3cf1fe35c44c81",
              "version_major": 2,
              "version_minor": 0
            },
            "text/plain": [
              "Extraction completed...: 0 file [00:00, ? file/s]"
            ]
          },
          "metadata": {},
          "output_type": "display_data"
        },
        {
          "name": "stdout",
          "output_type": "stream",
          "text": [
            "\n",
            "\n",
            "\n"
          ]
        },
        {
          "data": {
            "application/vnd.jupyter.widget-view+json": {
              "model_id": "9c71a40348394f9993b9a6afdb6d8ed7",
              "version_major": 2,
              "version_minor": 0
            },
            "text/plain": [
              "0 examples [00:00, ? examples/s]"
            ]
          },
          "metadata": {},
          "output_type": "display_data"
        },
        {
          "name": "stdout",
          "output_type": "stream",
          "text": [
            "Shuffling and writing examples to /root/tensorflow_datasets/fashion_mnist/3.0.1.incomplete5XTSD5/fashion_mnist-train.tfrecord\n"
          ]
        },
        {
          "data": {
            "application/vnd.jupyter.widget-view+json": {
              "model_id": "e9548d82467f471981626fdf90d5b84d",
              "version_major": 2,
              "version_minor": 0
            },
            "text/plain": [
              "  0%|          | 0/60000 [00:00<?, ? examples/s]"
            ]
          },
          "metadata": {},
          "output_type": "display_data"
        },
        {
          "data": {
            "application/vnd.jupyter.widget-view+json": {
              "model_id": "bc2348dcbde2414bb99729662a3763f5",
              "version_major": 2,
              "version_minor": 0
            },
            "text/plain": [
              "0 examples [00:00, ? examples/s]"
            ]
          },
          "metadata": {},
          "output_type": "display_data"
        },
        {
          "name": "stdout",
          "output_type": "stream",
          "text": [
            "Shuffling and writing examples to /root/tensorflow_datasets/fashion_mnist/3.0.1.incomplete5XTSD5/fashion_mnist-test.tfrecord\n"
          ]
        },
        {
          "data": {
            "application/vnd.jupyter.widget-view+json": {
              "model_id": "972c505f816d4414913fbb73cd2436fb",
              "version_major": 2,
              "version_minor": 0
            },
            "text/plain": [
              "  0%|          | 0/10000 [00:00<?, ? examples/s]"
            ]
          },
          "metadata": {},
          "output_type": "display_data"
        },
        {
          "name": "stdout",
          "output_type": "stream",
          "text": [
            "\u001b[1mDataset fashion_mnist downloaded and prepared to /root/tensorflow_datasets/fashion_mnist/3.0.1. Subsequent calls will reuse this data.\u001b[0m\n"
          ]
        }
      ],
      "source": [
        "import tensorflow_datasets as tfds\n",
        "\n",
        "dataset, metadata = tfds.load('fashion_mnist', as_supervised=True, with_info=True)\n",
        "train_dataset, test_dataset = dataset['train'], dataset['test']"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "YuIa7ZsscnDS"
      },
      "source": [
        "## Data information "
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 3,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "9zvtIOPeq9IF",
        "outputId": "7da3986a-3c3a-4e12-ac06-1bee9316a0c8"
      },
      "outputs": [
        {
          "name": "stdout",
          "output_type": "stream",
          "text": [
            "Number of training examples: 60000\n",
            "Number of test examples:     10000\n"
          ]
        }
      ],
      "source": [
        "num_train_examples = metadata.splits['train'].num_examples\n",
        "num_test_examples = metadata.splits['test'].num_examples\n",
        "print(\"Number of training examples: {}\".format(num_train_examples))\n",
        "print(\"Number of test examples:     {}\".format(num_test_examples))"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "iFp4-UU_hbAS"
      },
      "source": [
        "### Assign names to each class \n",
        "Currently we have class numbers `[0,9]`"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 4,
      "metadata": {
        "id": "5G7iTjkHhXsT"
      },
      "outputs": [],
      "source": [
        "class_names = ['T-shirt/top', 'Trouser', 'Pullover', 'Dress', 'Coat',\n",
        "               'Sandal',      'Shirt',   'Sneaker',  'Bag',   'Ankle boot']"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "h-UvDGFbhL1C"
      },
      "source": [
        "### Data visualization"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 5,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 589
        },
        "id": "D1TEwlTVhN1e",
        "outputId": "54bed8dd-787c-4dba-fad1-2c3711a59485"
      },
      "outputs": [
        {
          "data": {
            "image/png": "iVBORw0KGgoAAAANSUhEUgAAAj0AAAI8CAYAAAAazRqkAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADh0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uMy4yLjIsIGh0dHA6Ly9tYXRwbG90bGliLm9yZy+WH4yJAAAgAElEQVR4nOydd7hU1fX+322JXYqAAkoVRAVEQFQEFFFjjxq72JKfiRpLijWxRH2CmpjEr5poxChYYoyCqNgxgooFAamCqDSVjliwxXJ+f8zczbsX92zmXmfunbnn/TwPD2vm7Dlz5uyz9zl3vWut7ZIkgRBCCCFEQ2e9+j4AIYQQQoi6QA89QgghhMgEeugRQgghRCbQQ48QQgghMoEeeoQQQgiRCfTQI4QQQohMsEFNGjdr1ixp165diQ6lcD755BNvL1++3NubbbZZQZ//7LPPgtebbLKJt1u1avU9j664zJ8/HytWrHDF3m+59CXD5RMWLFgQbGvcuLG3v/nmG2/bvmzbtm2Jjq44TJo0aUWSJM2Lvd9y7M+GTpbGZhYoxdhUX9YPsb6s0UNPu3btMHHixOIc1Tr49ttvvb3++usH255++mlv33777d7u3bt30G6DDar/eS+//HLwulu3bt6++uqrU4+Jb8rOFX2uqxb7m4pFXfYln7fvvvsu2MZ9+9VXX3n7rLPOCtodeuih3l61apW3J0yYELT7xz/+Ue0x8PVkv7cucc4tWHermlOX/SlyNISxKdZQirGpvqwfYn0peUsIIYQQmaBGnp5iE/OcxP4SHz58uLfZdcgyFQA8+uij3t5000293bFjx6Dd3Llzvb169Wpvb7755kE7PsZCK1nXlUeovmEPznrrhc/SfA5i/brHHnt4e/bs2cG2+++/39vstbHnd8MNN/T2LbfcUtD3MuXiERJCCFF85OkRQgghRCbQQ48QQgghMoEeeoQQQgiRCeo1picW7zJ69Ghv22yrr7/+2tucyTNgwICg3cCBA6u1n3/++aDdjBkzvH3uued6+8QTTwza7bfffgUde1ZWruffaeN4mE8//dTbw4YNC7bdfPPN3uZ+7dWrV9CO+4hT1rt37x60e+aZZ7zdv39/bx9wwAFBu1NPPdXbbdq08baN4YnFKgkhhKgsNIsLIYQQIhPooUcIIYQQmaAk8lahRfxGjRrlbVtkjivtcro5EBYF+/DDD709ffr0oN2YMWO8/cUXX3h7yZIlQbt+/fp5m1OWR44cGbR76qmnvM3p7FdddVXQLpbaXskp7LawYJrcc9lllwWvH3jggdR92rIAVdjyAxtttFG12/h9IKzczJW77TFw326//fbeHjp0aOr+WFYD0otfCiGEKE/k6RFCCCFEJtBDjxBCCCEyQUn88yyD2GyYWbNmeZvlp2222SZo16xZM29beYurJm+77bbe3mKLLYJ2LFuwFNOnT5+g3ZdfflnNrwAaNWqU2m7evHnevvbaa4N2l156abX7q3Ri2Uuc9XbPPfcE29q3b+/tjTfeONjWpEkTb7N81LJly6Dd//73P29vueWW3t5uu+2Cdp9//nm1x2clTd4fZ4YdeeSRQTvO9LNyVn2sxSaEEJUOz79AGN5i10885JBDvH388cd/7++Wp0cIIYQQmUAPPUIIIYTIBHroEUIIIUQmKElMT2xl6hEjRnh7s802S23HsRlcqRdYO3U67X1egZ1jSWwMz1dffeVtTlmPVeflWCIbLxLbR6URi1vhbU888YS3u3TpErRj/damffM++FwtX748aMexPz/4wQ+8/cEHHwTt+Frh/uISCED4Wzh+iGPOAGD48OHe5irO9tgV0yNEnPnz53v7ySef9PZZZ51V0OdtHAjH2Nnxp/FYP3BpGAC47777vP3ggw96m68FILxXz5kzJ3X/iukRQgghhCgQPfQIIYQQIhPUeUlZrpLLLkhelNJiq/amVTy21Y9Z3uDPWBccf46Pg2UvIHSvsjRn3a5cGbpHjx6p31XpLtjf/e533t5www29bVP9Fy1a5G1bfoAlLXZX2/R4lqe4IrNNgecKzR9//HG1x2ePqXnz5t62pRPYDW/lLS1AKkT6orxWyuYFod977z1vP/7440E7XmyaYVm7GMcn1mbu3Lne5jANew8eN26ct//2t795294L+TWHEey1116px2Cr8fN9eNmyZd5u0aJF0I6PN4auACGEEEJkAj30CCGEECITlFzeYncUACxevNjbHTp08LZ1TS1YsMDbXNEXSM/6slIHu8VYOrGLVHLGDx+HzfJiiSWWlfXss89628pblSZpxY739ddf9zZXSbay4FZbbZW6jatrc0Vt64bm/fNnrMubPxfLBmvatKm32QVr3bh8HYq657XXXvM2V/r+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8d2qVStvP/bYY0E7jic75phjqvkVoqakVZ3/4IMPgtdpMadc6gEIV0Xg/po2bVrQju+TPPZs3A7Pu1zCAgjHNlcNr211Znl6hBBCCJEJ9NAjhBBCiExQcnlr8uTJwWtO72aXqXV/swvVylHsguN21mVmZacqrKuP5SiW0mxF0VmzZnmb3bN2MUX+LXYR1CzKW7EFPd966y1vH3744ant0tITY2mLHTp08DYvbluT48sSLE3wNR2Tl+0YSyvrEDvHPF6svMhjMG0822NibMVZniNsui7LeLZMRkPBzmksE9oyESxV/OIXv/D2iBEjgnbXXHONt7mSOocDAGH1dJb9raRiZbYqYteaiJM2Pp555pngNUtVvCJBmzZtgnY8Zvm+aCugb7PNNt5mKc1KpHacph0TV+WWvCWEEEIIEUEPPUIIIYTIBCWXt957773gddOmTb3NGVs2OtwucsiwS5Zdo9bdye240qR1rfF384J51j3LmV2clWarnPIxcXXRrFKoG9pmljDcl+xaje27W7du3uaqsbF9Z5m0Sstc2RwIK5XHsrJipLWzEgb3Dfd17Hv4d9hjZ3c7Vw8GQjmnV69eqfuvZGJysJUW586d622uls6VzgHg5ptv9jbPn5dffnnQjhdfPuqoo7xtpY3OnTtXe3wap4Vjx0dav9vwC66UzGORxxQAPP74495u1qyZt21GJN9DY3I3Z2HbY2dJliV4ex3yNRVDV5EQQgghMoEeeoQQQgiRCfTQI4QQQohMUJKYHq7saldN5riYMWPGeNtq74WmjLIOHavIzFUerTbMMQqsH9qVYDfddFNvN2rUyNs2XqRdu3befvfdd4NtnB5vY4YqmViMRSyOwK54nwbHmBQa0xNb0X7GjBne5kqxWU6L5erFPEZWrlwZtOP4jp122inYxuUlCo3B4HaFrpwcS0WfPXu2t+08wteETd/OQkxPDI63BIC2bdtWu+3YY48N2o0ePdrbJ510krebNGkStOPUY75ubGxV2nVT21W1s0ihMT32Hsf9zHOznQN4f1x12c65vDo7l76wcbV8/7clMvgez2n0d911V9BOMT1CCCGEEIQeeoQQQgiRCUoib3GaunVVpslCtuoyu6utxMCvC118kl1mtl1aWqxN4WQ33pw5c7xtXXUsl9jF0zhFkBc6bUhY2YDPKct7wNryZxXWxclu05ib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",
            "text/plain": [
              "<Figure size 720x720 with 25 Axes>"
            ]
          },
          "metadata": {},
          "output_type": "display_data"
        }
      ],
      "source": [
        "plt.figure(figsize=(10,10))\n",
        "i = 0\n",
        "for (image, label) in test_dataset.take(25):\n",
        "    image = image.numpy().reshape((28,28))\n",
        "    plt.subplot(5,5,i+1)\n",
        "    plt.xticks([])\n",
        "    plt.yticks([])\n",
        "    plt.grid(False)\n",
        "    plt.imshow(image, cmap=plt.cm.binary)\n",
        "    plt.xlabel(class_names[label])\n",
        "    i += 1\n",
        "plt.show()"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "9MP-9Ph0dF3V"
      },
      "source": [
        "## Data preprocessing"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "Exa7E1dwhtXh"
      },
      "source": [
        "### Data normalization"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 6,
      "metadata": {
        "id": "I0tX90gJdJRz"
      },
      "outputs": [],
      "source": [
        "def normalize(images, labels):\n",
        "  images = tf.cast(images, tf.float32)\n",
        "  images /= 255\n",
        "  return images, labels\n",
        "\n",
        "# The map function applies the normalize function to each element in the train\n",
        "# and test datasets\n",
        "train_dataset =  train_dataset.map(normalize)\n",
        "test_dataset  =  test_dataset.map(normalize)\n",
        "\n",
        "# The first time you use the dataset, the images will be loaded from disk\n",
        "# Caching will keep them in memory, making training faster\n",
        "train_dataset =  train_dataset.cache()\n",
        "test_dataset  =  test_dataset.cache()"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "A3D3Q2nLiVft"
      },
      "source": [
        "## Building the model"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 7,
      "metadata": {
        "id": "5-nTUTq6iXOl"
      },
      "outputs": [],
      "source": [
        "model = tf.keras.Sequential([\n",
        "    #  A convolutional layer that applies 32 filters with a kernel size of `3x3`\n",
        "    tf.keras.layers.Conv2D(32, (3,3), padding='same', activation=tf.nn.relu,\n",
        "                           input_shape=(28, 28, 1)),\n",
        "    # A MaxPooling layer for 2D data that downsamples the input data \n",
        "    tf.keras.layers.MaxPooling2D((2, 2), strides=2),\n",
        "    tf.keras.layers.Conv2D(64, (3,3), padding='same', activation=tf.nn.relu),\n",
        "    tf.keras.layers.MaxPooling2D((2, 2), strides=2),\n",
        "    # Flattens the input data. e.g., if we have a 2d array with the following dimensions: [10, 10] it will converted into [1, 100]\n",
        "    tf.keras.layers.Flatten(),\n",
        "    # 128 units (i.e., neurons) / The Activation function is the ReLU\n",
        "    tf.keras.layers.Dense(128, activation=tf.nn.relu),\n",
        "    tf.keras.layers.Dense(128, activation=tf.nn.relu),\n",
        "    # 10 units (because there exist 10 classes) / The Activation function is the Softmax \n",
        "    # (frequently used in multinomial classification problems)\n",
        "    # Calculates the probability of an input data to be classified in either one of each class\n",
        "    # The sum of all probabilities is equal to 1. \n",
        "    # The object is classified to the class with the highest probability\n",
        "    tf.keras.layers.Dense(10, activation=tf.nn.softmax)\n",
        "])"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "JYRDxyB2la1J"
      },
      "source": [
        "### Compile neural network"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "vN2KE_7oljos"
      },
      "source": [
        "* Optimizer: Adjusts the inner parameters of the model in order to minimize the loss\n",
        "* Loss (i.e., loss function): Measures how far away the predicted output is, from the desired output\n",
        "* Metrics: We use accuracy in order to test how many of the test data are correctly classified"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 8,
      "metadata": {
        "id": "HFiiNheOlajO"
      },
      "outputs": [],
      "source": [
        "model.compile(optimizer='adam',\n",
        "              loss=tf.keras.losses.SparseCategoricalCrossentropy(),\n",
        "              metrics=['accuracy'])"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "RE5YihkdmRe5"
      },
      "source": [
        "## Training the model "
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 9,
      "metadata": {
        "id": "SS9S3sUKmQ5N"
      },
      "outputs": [],
      "source": [
        "BATCH_SIZE = 32\n",
        "train_dataset = train_dataset.cache().repeat().shuffle(num_train_examples).batch(BATCH_SIZE)\n",
        "test_dataset = test_dataset.cache().batch(BATCH_SIZE)"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 10,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "yRljFmyammrP",
        "outputId": "9484c3a0-991c-4fe3-cb33-c84195231c86"
      },
      "outputs": [
        {
          "name": "stdout",
          "output_type": "stream",
          "text": [
            "Epoch 1/10\n",
            "1875/1875 [==============================] - 22s 3ms/step - loss: 0.4088 - accuracy: 0.8516\n",
            "Epoch 2/10\n",
            "1875/1875 [==============================] - 6s 3ms/step - loss: 0.2652 - accuracy: 0.9027\n",
            "Epoch 3/10\n",
            "1875/1875 [==============================] - 7s 4ms/step - loss: 0.2093 - accuracy: 0.9230\n",
            "Epoch 4/10\n",
            "1875/1875 [==============================] - 6s 3ms/step - loss: 0.1836 - accuracy: 0.9312\n",
            "Epoch 5/10\n",
            "1875/1875 [==============================] - 6s 3ms/step - loss: 0.1542 - accuracy: 0.9427\n",
            "Epoch 6/10\n",
            "1875/1875 [==============================] - 6s 3ms/step - loss: 0.1328 - accuracy: 0.9503\n",
            "Epoch 7/10\n",
            "1875/1875 [==============================] - 6s 3ms/step - loss: 0.1137 - accuracy: 0.9581\n",
            "Epoch 8/10\n",
            "1875/1875 [==============================] - 6s 3ms/step - loss: 0.0988 - accuracy: 0.9636\n",
            "Epoch 9/10\n",
            "1875/1875 [==============================] - 6s 3ms/step - loss: 0.0815 - accuracy: 0.9693\n",
            "Epoch 10/10\n",
            "1875/1875 [==============================] - 6s 3ms/step - loss: 0.0723 - accuracy: 0.9738\n"
          ]
        },
        {
          "data": {
            "text/plain": [
              "<keras.callbacks.History at 0x7f54701ff050>"
            ]
          },
          "execution_count": 10,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "model.fit(train_dataset, epochs=10, steps_per_epoch=math.ceil(num_train_examples/BATCH_SIZE))"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "OwUtUEAcm_mr"
      },
      "source": [
        "## Evaluate model (accuracy metric)"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 11,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "j8J1SQZgnB6Y",
        "outputId": "f9167809-3885-45d1-a50b-99039cf011fc"
      },
      "outputs": [
        {
          "name": "stdout",
          "output_type": "stream",
          "text": [
            "313/313 [==============================] - 2s 6ms/step - loss: 0.3358 - accuracy: 0.9181\n",
            "Accuracy on test dataset: 0.9180999994277954\n"
          ]
        }
      ],
      "source": [
        "test_loss, test_accuracy = model.evaluate(test_dataset, steps=math.ceil(num_test_examples/32))\n",
        "print('Accuracy on test dataset:', test_accuracy)"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "U9Dj9qDe7vil"
      },
      "source": [
        "## Make predictions "
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 12,
      "metadata": {
        "id": "j-83Rv2M7u8R"
      },
      "outputs": [],
      "source": [
        "for test_images, test_labels in test_dataset.take(1):\n",
        "  test_images = test_images.numpy()\n",
        "  test_labels = test_labels.numpy()\n",
        "  predictions = model.predict(test_images)"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 13,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "qFSoz6L_74vq",
        "outputId": "8ab4deeb-13c2-4d22-86e2-172dc2414b08"
      },
      "outputs": [
        {
          "data": {
            "text/plain": [
              "(32, 10)"
            ]
          },
          "execution_count": 13,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "predictions.shape"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 14,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "MMv9O8d376tg",
        "outputId": "8b760759-1ddf-45b4-e4ba-7d333703f65f"
      },
      "outputs": [
        {
          "data": {
            "text/plain": [
              "array([3.81634936e-06, 7.64805066e-07, 3.13659990e-03, 9.40445261e-06,\n",
              "       9.31403279e-01, 2.00955057e-08, 6.54460788e-02, 2.01350914e-09,\n",
              "       1.02407895e-07, 2.54411141e-08], dtype=float32)"
            ]
          },
          "execution_count": 14,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "predictions[0]"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 15,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "nKpOIREk79fO",
        "outputId": "0cbe1259-2877-447e-a15a-a23a7ec7f4ec"
      },
      "outputs": [
        {
          "data": {
            "text/plain": [
              "4"
            ]
          },
          "execution_count": 15,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "np.argmax(predictions[0])"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 16,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "qRjhJsk58CGh",
        "outputId": "e9583024-9084-4d0e-866b-93d75f42ec96"
      },
      "outputs": [
        {
          "data": {
            "text/plain": [
              "4"
            ]
          },
          "execution_count": 16,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "test_labels[0]"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 17,
      "metadata": {
        "id": "UqoRsJNU8FHu"
      },
      "outputs": [],
      "source": [
        "def plot_image(i, predictions_array, true_labels, images):\n",
        "  predictions_array, true_label, img = predictions_array[i], true_labels[i], images[i]\n",
        "  plt.grid(False)\n",
        "  plt.xticks([])\n",
        "  plt.yticks([])\n",
        "  \n",
        "  plt.imshow(img[...,0], cmap=plt.cm.binary)\n",
        "\n",
        "  predicted_label = np.argmax(predictions_array)\n",
        "  if predicted_label == true_label:\n",
        "    color = 'blue'\n",
        "  else:\n",
        "    color = 'red'\n",
        "  \n",
        "  plt.xlabel(\"{} {:2.0f}% ({})\".format(class_names[predicted_label],\n",
        "                                100*np.max(predictions_array),\n",
        "                                class_names[true_label]),\n",
        "                                color=color)\n",
        "\n",
        "def plot_value_array(i, predictions_array, true_label):\n",
        "  predictions_array, true_label = predictions_array[i], true_label[i]\n",
        "  plt.grid(False)\n",
        "  plt.xticks([])\n",
        "  plt.yticks([])\n",
        "  thisplot = plt.bar(range(10), predictions_array, color=\"#777777\")\n",
        "  plt.ylim([0, 1])\n",
        "  predicted_label = np.argmax(predictions_array)\n",
        "  \n",
        "  thisplot[predicted_label].set_color('red')\n",
        "  thisplot[true_label].set_color('blue')"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 18,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 203
        },
        "id": "ccBt153s8H3g",
        "outputId": "209d1598-aa3c-4cc5-e6eb-42605407795a"
      },
      "outputs": [
        {
          "data": {
            "image/png": "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",
            "text/plain": [
              "<Figure size 432x216 with 2 Axes>"
            ]
          },
          "metadata": {},
          "output_type": "display_data"
        }
      ],
      "source": [
        "i = 0\n",
        "plt.figure(figsize=(6,3))\n",
        "plt.subplot(1,2,1)\n",
        "plot_image(i, predictions, test_labels, test_images)\n",
        "plt.subplot(1,2,2)\n",
        "plot_value_array(i, predictions, test_labels)"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 19,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 203
        },
        "id": "Tn0rVtRC8KTD",
        "outputId": "0182abb4-9283-47f2-871f-8fa7db9a10d3"
      },
      "outputs": [
        {
          "data": {
            "image/png": "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",
            "text/plain": [
              "<Figure size 432x216 with 2 Axes>"
            ]
          },
          "metadata": {},
          "output_type": "display_data"
        }
      ],
      "source": [
        "i = 12\n",
        "plt.figure(figsize=(6,3))\n",
        "plt.subplot(1,2,1)\n",
        "plot_image(i, predictions, test_labels, test_images)\n",
        "plt.subplot(1,2,2)\n",
        "plot_value_array(i, predictions, test_labels)"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 20,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 589
        },
        "id": "Ex-HgKPu8M7H",
        "outputId": "e484bfe0-02df-43d1-99ab-d9971919ae3f"
      },
      "outputs": [
        {
          "data": {
            "image/png": "iVBORw0KGgoAAAANSUhEUgAAAsQAAAI8CAYAAAD2lL33AAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADh0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uMy4yLjIsIGh0dHA6Ly9tYXRwbG90bGliLm9yZy+WH4yJAAAgAElEQVR4nOzdd5wV1f0//tcbpC8sZZdelqog0sFCURSNxm7UaEQl5mcs0WhiYiS2RH+xxHxSLCmWBDTGGAQJFlSCiooCsvQOUqT33sHz/WNmz77P4c5wWbbc3Xk9Hw8evO+dc+fOLefO7Jz3vI8YY0BERERElFSVynoDiIiIiIjKEg+IiYiIiCjReEBMRERERInGA2IiIiIiSjQeEBMRERFRovGAmIiIiIgS7YSy3oCcnByTl5dX1puBHTt22Hjjxo02rlWrVlqP3717t3O7Ro0aNm7atOlxbl3xy8/P32SMyS2u9WXK55hUSfg8dYnIFStWOMvq1q1r40OHDtnY75etWrUqoa0rHkn4HJOCn2XFwM8xs82cCaiffMcJJwBdu7r3xX2eZX5AnJeXh6lTp5bKcx0+fNjGlStXdpa9//77Nn7++edt3KtXL6fdCSekfss+//xz5/Ypp5xi40ceeSRym/ROXkQi2xU3EVlx9FbpK83PkY5Unj9P3Qe++eYbZ5nup/v377fxbbfd5rS76KKLbLx161YbT5kyxWn3t7/9LeU26N8G/3lLU3n+HMnFz7Ji4OeY2eIOmw4dAvy3Ou7zZMoEERERESVamZ8hLm5xZ1zjzvoMHz7cxno4Q6c+AMCYMWNsXLNmTRu3bdvWabd06VIb79q1y8ZZWVlOO72N6c4aWJpnkomKgz7zW6mS+3e4/j7H9dHTTjvNxgsWLHCWvfbaazbWZ3v9vlKlShUbP/vss2k9r5YpZ5KJiKh48QwxERERESUaD4iJiIiIKNF4QExEREREiVbhcojj8mvffvttG/tVIQ4ePGhjfZX6gAEDnHYDBw5MGX/00UdOuzlz5tj4zjvvtPH3vvc9p92gQYPS2vZ084sptcaNgfXrUy9r1AhYt650tycJ9HfWzxvWdu7caeNhw4Y5y5555hkb6z7as2dPp53ub7rsWpcuXZx2H3zwgY379+9v4/POO89pd+ONN9q4ZcuWNvZzhuNyo4mIqPzgLzglQtTB8NGWERERUcXHA2IiIiIiSrRykzKR7gQWo0ePtrFflF/PWqVLpgHuBBxbtmyx8ezZs512//vf/2y8d+9eG6/zxtz79etnY12qadSoUU679957z8a6JNuvf/1rp11ceTaWYaNM4E+qEZVC8MADDzi3X3/99ch1+mUKC/jlEKtVq5Zymb4fcGe007NT+tug+2m7du1s/MILL0Su75A3XVLUJD5ERJR5eIaYiIiIiBKNB8RERERElGjlZkxPD8f6V3rPnz/fxjqloXHjxk67nJwcG/spE3o2uebNm9u4du3aTjs9fKqHhPv06eO027dvX4pXAWRnZ0e2W7ZsmY0ff/xxp93QoUNTro8oU8RVWdCVVl555RVnWevWrW1cvXp1Z1m9evVsrFMSmjRp4rQ7cOCAjevUqWPjFi1aOO327NmTcvv8lCe9Pl3B4vLLL3fa6eoyfopEumleRERU9niGmIiIiIgSjQfERERERJRoPCAmIiIiokQrNznEft6wNnLkSBvXqlUrsp3OH9SzXgFHloyKuj8vL8/GOt/Rzxnev3+/jXXZtbiZrnTusp/TGLcOorISlyerl7377rs2Pumkk5x2Ol/XL12m16G/9xs3bnTa6VzjqlWr2nj16tVOO93vdd/TJRkB97XofGV9vQIADB8+3MZ6djt/25lDTESU2XiGmIiIiIgSjQfERERERJRo5SZlIo6ecUoPTe7cuTPyMf4MWFEzwfmzwulhVv0YPWud/zi9HTqVAnCHi3W6h74fcGfM69atW+RzcWiWMsX9999v4ypVqtjYLz24Zs0aG/vlEHWahC5r5pd40ykPeqY6v4ybnrlu+/btKbfP36bc3Fwb+6Ucx44da2M/ZSKuDB0REWUW/mITERERUaLxgJiIiIiIEq1cpkxs2LDBub127Vobt2nTxsa6MgMArFixwsZ6diwgujqFP+SqUx70EK4eigXcq9n1dvjVKPRQb1z1iHHjxtnYT5lgmgSVlbjv3pdffmljPXucnzbUoEGDyGV6Bkk9a6SfjqDXrx+jK074j4urWlG/fn0b6/QlP9VK/6YQ0bGbPHmyjfUsljfddJPTrkePHiW2DX71mGbNmpXYc1Hm4hliIiIiIko0HhATERERUaLxgJiIiIiIEq1c5hB/9NFHzm2dh6vLNi1fvtxpF1XizH+czi1MN4fYz2nUOcR6Hf7zrl+/3sY691HnVQLAggULQJTJ9PcXADZt2mRjPdvb9OnTnXYdO3ZM2Q5wc3T1TI7+TJO6tKHub345Nb1s27ZtNm7UqJHTTpdX1Nvr5zFu2bLFxitXrnSWtWjRAkQVWXGU/NT7Nj2b7Isvvui0u+aaa2ysZ4z1r9+pW7eujfW1N4B7/ZHe3vbt2zvt/GMMSgaeISYiovKrcWNAJPU/r240EVEUHhATEVH5pUbZjmkZEZFSLlMm5s2b59zWQyR6Jik97AkAU6ZMsfGpp57qLNMpClGzYwHu0KwuwaTLPgHukK5Op/DTOPSw7RlnnGFjf+Y73U4PRQNATk4OiMrae++959zWM0i2atXKxv4sjF988YWNL730UmfZiSeeaGM93Hno0CGnnU6N2Lp1q439/qtv6xnt/P77zjvv2Fj3Zb1uwP09mDRpkrOMKRNU0cWlSaSbTjFz5kwb69KKfhlSnVqxZMkSG/t9Uh8PLFu2zFm2dOlSG+v0RT+1asCAAZHbSxUXzxATERERUaLxgJiIiIiIEo0HxERERESUaOUyh9jPGdL5STrfT+cwAu70jKtWrXKWReUu+WXS9DI/R1nT26HLUU2bNs1pp6e31XnNflkpnVM8ceJEZ5mfd0lUFj755BPnts5t13nDfg6xLpvkT4Xcrl07G+sShf707bpsks5d9HMIdT6/ztnXOfqAm1+sp1v3cw11nrD/+q+66ioQVWRxecJRecN+H9el1urVq2fjxl6FEH2dj94/6r4KxJdN1VO56zKOgwcPTrmtlCw8Q0xEREREicYDYiIiIiJKtHKZMqFnpgOAZs2a2Tg7O9vG/jCoTjvwh23atGljYz1E6qcu6CGiw4cP29gfwt24cWPKbdfrBtxhoNNOOy3yefVz+bPWMWWCMoGfyqO/s/p776dMdO/e3cb+bHe6rJlOn/BnhtRl2PQyv5yaHpLVz7Vo0SKn3QUXXGDjMWPG2Hjz5s1OO5029dVXX4EoSYoyO927777r3NalEHV/0rPHAm4f17GfuqjLoW7fvt1ZpmeT7N+//7FsNiUAzxATERERUaLxgJiIiIiIEq1cpkz4VSZatmxpY52qoIdbAaBz58429odZ9DCuHqrxr1LVaRc6rUHPjuOvXw8X++vT6R/5+fk29mfp0evw0z2IMsHXX3/t3O7du7eN165da2M/ZeL222+38WOPPeYs06kM+grx/fv3O+38K80L+KlHOk1CL1vvTfHbunVrG+u+uGXLFqddXl6ejf3KNUTlhU4FBIqWChG3Dj27rD9bq+7XcbPH+elU6fBntNTpGbm5uce8PqrYeIaYiIiIiBKNB8RERERElGg8ICYiIiKiRCs3OcS6XIo/e1ynTp1srHMB/bxeXY7FzyHWubx65hw/B1E/Tuco+zm/uuSbLv3i5yCecsopNtY5Ul27dnXa6fX7ZeeIMsGmTZuKtKxXr1421n0PAPr162djPaOd3weWLFliY91XdKk2wP0N0L8Pc+fOddrpme/0NQV+eUXdZ6NKLRIVl4I83aLk+JY0f5t0icJx48bZWPdjwN2P6rKIOt8XcPfFej/s78t1//fzkPXvhj+LJRHPEBMRERFRovGAmIiIiIgSrVymTPjDpXrI5csvv7TxRRdd5LTTqQv+0Kwe7tGz3fmpELq0jB76qV27ttNOp0zoMlP+DFsDBw60sR5+1WVqfByapUyhU5QaN27sLNNDnP6MUVrULJEAsHjxYhvr0mq6/CHg9kv9vPp3A3Bnz8vJybHxjh07nHYnn3yyjVu0aGFjv7Ra1O8G4Jaaa9KkCYiOV0mlShTHetetW+fcnjZtmo11v/NnkNWlSPXMrX4qhN536lQIv4yjfpxOwfBvx6VxUTLxDDERERERJRoPiImIiIgo0cpNyoROE/CrTOgZZ3SKw2mnnea001e6+qkLmh5y9a9SjVqmh4T8ZTr2Z8/Tw7E6ZcKfjU/P5uMvIyorOrXH7wO6r+jY7796yNSv6qKrPei0CH84Vc/eqNMp9IxzgFsxQqc56eFdwJ3V8swzz7TxJ5984rTTqSD6qnrAfW+YMkElKarqQtx+TqdJFDVlQldd8WdQ1ZVf9Ixx/qySutJSw4YNbezvK/Xr0hUo/GoUul/7s+fpZf7slEQ8Q0xEREREicYDYiIiIiJKNB4QExEREVGilZscYp0365dLiSrp5Jd30TlDenYswJ21Spd1279/v9NO5zjqXCg/91HnU+pSLyeeeKLTbubMmTZu27atjdesWeO007nG/nMRlRXdV/zcYF1CTce61CDg5hf6fVbf1jn2fpm0qLxJvxSUbte0aVMb+33q7bfftvFZZ51l40cffdRpp3MU/esNVq9eDaLSoL/zcXnDReGX+dR9SvdJfY2Or06dOjbWOcMA0KpVKxvrXHt/v67Lq+n+6ucJ6+uI/GsNdL6xzpv2S7fpa3YoOXiGmIiIiIgSjQfERERERJRo5SZlQg/NtGzZ0lmm0x2aN29uY78Mkh4W8Yd39axzeghGl4QCjpxJq4BfckqvX5eP8bc9qvSLP/x60kkn2Xjs2LHOMj3k7JegISpJOnXBn0HS7xMFdAoC4A61+rO9NWrUyMa6ZJIutQi46Ql6yNhfnx5O1SlPXbp0cdoNHz7cxoMHDz7yRYT00G1WVlZkO6KSpPvalClTbKzLDALRM8H5M7LqfaW/TJdX06XVdAoS4O479fo6derktNOzxk6YMMHGfiqEPgZYuHBh5PbpfuinPDZr1izlMr/Em36fKDl4hpiIiIiIEo0HxERERESUaOVmfF1XmdApAgAwY8aMlMuWLl3qtNNDRP5VpHrYRg+D+le66uFYnZ7gDxfrx+nn9Yd6FyxYkHJ7/e1bvny5jf0r7PX2MmWCSpP+bvuzwvn9tECbNm2c2zplQl+NDrj98uuvv45ctx7+1P3BT3HyU6UK6NQM/7l0lRidWgW4Q9X+8OyqVatSPhdRUezevRuTJ08GAFxwwQXOsgsvvNDGOlXQr1bUuHHjlO169+7ttNNpB/73WPcB3V/9vqF/D+rXr29jnY4EuJWWdF/Lyclx2un9nk7b8H939AyR/jLdXxcvXmxjnXZJycUzxERERESUaDwgJiIiIqJE4wExERERESVauUk41bPK5OXlOcv07G8rV6608aRJk5x2nTt3trE/I5YuGaPLxfgz3WzYsMHGOk/YL++kSzrp8jH+LHs6d0mXkhkwYIDTTuc4+nmQW7ZssbEuK0NU0vR3T/cNwM2D17ntfjmlzz77zMbdunVzlulcYd3H/Fx53a90nqCfsx+1HX6f0mWYdGkpP09YP5eeZStVW6LjsXr1agwdOhQAsHfvXmfZm2++aWOdy+vnxurvvL4eRn/HAbc0mr+v1H1y2rRpNtZ59/7j9G/BGWec4bTr3r27jfV+3s9J1iXk9OvyX6Pe9/rl03TesM5X9ku3UTLxDDERERERJRoPiImIqNQ1bgyIRP9TBRGIiEpcuUmZ0EMd/jCITpPQaQx+uRidMqGHiwC3BI2eJc4vf6ZLOukhHX/IRZd70sPK/sxB+rn0bFsbN2502unX7M/Ap0vSMWWCSpMegm3RooWzTH+f9TCrX6Jw2bJlNvbTDvTQsH6c7oeA29/0sOvatWuddnqYVKdP+P1S9yldGtGfQVK/Lj9Fwi95Ra6ISTrTXp40HTp0wPjx4wEA06dPd5aNGDHCxnrZ3LlznXb6u6z7ib4fAObMmWNjnYIAuDPG6T7pz9SoS57plD8/bVCnNur+r0uNAu5+T6c46tKMgPtb4JdN1eXf9D7bP1bQM95ScvAMMRERERElGg+IiYiIiCjRyk3KhE5x8IczOnToYGM9/OKnVughUn/IVc+4o2fE8YdB9fCMvhJdD7EC7lCyHnLyUyH0NukZvPwrbPWVtP7QtP/cRKVFpwWs98a4dd/R31+/T8X1S52SoGfZ8tMudGqEHgqOm4HqwIEDNvb7pa40o4dd/d8Uvb36eYEjK9QQHa+C71iPHj2c+/3bBfyUAZ3GNHv2bBv7s7rqND8/HVCnF+kqLv5sj3p/Vrt2bRv7aYg6/UE/10cffeS0e/rpp23csGFDRImajRJwUyZ0H/f7NSUTzxATERERUaLxgJiIiIiIEo0HxERERESUaOUmh1jnNPllVnQ+4eTJk22s84IBN6cpPz/fWda+fXsb5+Tk2FjnMALAV199ZWM9c5ZeN+DmSeqc5HXr1jntdK6wLivjzxzUtm3blO0AYMWKFTbu378/iEqLziH0c/sXLVpk45YtW9rYn/lK5xD7Zc30d13n7OvST4Cbv6vX4c/oFTVTlz+jnV6HzjX0Z8nUJR91O+DI8lJEpc2fQVXf1rPRZaKBAwfG3iYqbjxDTERERESJxgNiIiIiIkq0cpMyoYdZ/Rlx9JCrjv10B5264A+RRs3M45dS0mVhdOrGzJkznXaHDx+2sS6/pMvPAO4wsB6m9dvpZX4pKX9YmKi0zJgxw8Z+KTSdnqBniFu4cKHTTqco6ccA0WXT/LKEug/oVAg/BUP3X13+yX9e/RujS7r5aVj6ufyUCV3iiYiIMhvPEBMRERFRovGAmIiIiIgSjQfERERERJRo5SaHWOcG6xxfwM3x03m9F198sdNO5wn7oqaP1M8LuFPVan6+YFSu8fz58512etrpnj172nj8+PFOu0GDBtnYz2v2y9ARlRb93fP7iu4DuuyazrsFgHnz5tlYT88MuHm+eqrl5cuXR7bTsd83dGk4ndvvTxm9YMECGzdr1izlY3x+Lv++ffsi2xIRUWbhGWIiIiIiSjQeEBMRERFRopWblImaNWva2C+lpMuptWvXzsa333575Pr0DFMAsH37dhtv3brVxrVq1XLaLV682MZ66Ncvk6aHbZs0aWJjPfwKHFnGqcCECROc2zpVw98mf+Y6otKiUwh0igTgpvboVIXHHnvMaTds2DAb6xkeATftQJdR9NMTdJ+IK72ot0mnXvll3KJcffXVzm39+v11RKVXERFR5uEZYiIiIiJKNB4QExEREVGilZuUCX1VuZ4FDgBWrFhhY30lepwWLVrE3o7So0ePtNodLz8tRM/U5/OHmYlKy/Tp023sV4jQszBu2rQprfX5aQfppjKUFj/lacOGDTbWs/EBbioXERFltnJzQEyUCe67777IZU888UQpbgkREREVF6ZMEBEREVGi8YCYiIiIiBKt3KRMfPvb37bxqlWrnGU63/b73/9+5DqMMZHL/LzkAn4pKU2XcPLLO0W1i1ufduKJJzq3169fb2N/pi89ix1RafrjH/9o49WrVzvLZs2aZeO4VJO42d/0srj+my6/7xTwZ3/Ut3X85JNPOu1OOeUUG2dlZTnLSut6AyIiOn48Q0xEREREicYDYiIiIiJKNCmOYcjj2gCRjQBWHLUhFbdWxpjc4loZP8cyx8+zYuDnWHHws6wY+DlWLJGfZ5kfEBMRERERlSWmTBARERFRovGAmIiIiIgSLaMPiEXQWAT/FsFXIsgXwbsi6FCE9dQVwe0xy+8SwRwRzBXB3er+R0UwSwQzRPCBCJqG938nbPupCBqE97UVwesxzyEi+FAEdUrytYkgVwTvHet6iNIicj9E5kJkFkRmQOTU8P7lEMlJ0f4SiKSuuSZyFkTOiFj283D9MyAyByKHIVI/XHY+RBZCZImzbpFXw+16TN33AEQui3k93SHykrp9AUSmQmQeRKZD5P9i3o1o/msTuQMiNxVpXZTxRHCZCIwITkqz/XIRHNFfRLDrGJ/3mNrHrGdIwf4txbKrwv3dNyLo5S0bKoIlIlgogm+p+88P71sigvvU/a+G+9TH1H0PiCCyj4qguwhe8u4bLYJJab62s0TwdsRrfjaddRSlfcx6uM/OUBl7QCwCAfAmgI+NQVtj0BPAUACNirC6ukDqA2IRdAZwM4A+ALoCuEgE7cLFTxmDLsagG4C3ATwU3n8ngN4A/gbge+F9/z+AB2K24dsAZhqDHSX52ozBRgBrRdC3COsiiiZyOoCLAPSAMV0ADAKwMvYxxoyBMUfOaS1yAoCzAKQ+IDbmKRjTDcZ0Q9A3JsCYLRCpDOA5ABcA6ATgWoh0gkgXAHvD7eoNkWyINAFwKowZHbOFvwTwdLhNnQE8C2AwjOkEoBeAJbGvL5r/2v6O4HeDKqZrAXwW/l8eDQFSHxADmAPgCgCf6DtF0AnANQBOBnA+gD+LoLIIjuijIugkgi4A9hqDLgB6iyBbBE0AnGoM0uujwfPWBdATQLYI2hz7Sy1z3GdnqIw9IAYwEMBBY/DXgjuMwUxj8Gl4tvWp8KzubBF8FwBEkCWC8SKYFt5/afjQJwC0Dc/0PuU9T0cAk43BHmNwCMAEBJ0fxmCHalcLQMEViN8AqAagJoCDIugPYJ0xWBzzeq4D8N9Sem2jw+cjKk5NAGyCMfsBAMZsgjFr1PI7ITINIrMhEpwpExkCkWfDeBhE/gqRyQD+A+BWAD8JzwL3j3neawG8FsZ9ACyBMUthzAEA/wZwKYCDAGpApBKAKgAOA3gEwMORaxWpDaALjJkZ3nMvgN/AmAXh6zsMY/4Sts2DyIfhGejxEGkZ3n8xRCaHZ5P/B5FGEMk74rUZswfAcoj0iXmdVA6JIAtAPwA/QHCAWHD/WSL4WARviGBBeHZUvMfWEMFYEdycYr0/F8GX4RnVX8c8/x/CM7jjRZAb3tdNBJPCx74pgnpR94vgSgR//L0a7kdq6PUbg/nGYGGKp74UwL+NwX5jsAzBH499wn9LjMFSY3BEHxVB2n1UBLUBdDEGM9XdVwB4K1yvfr+HieBpEXwugqXh6/LX11sE00XQ1rs/VwQjw/f7y5iD0xbhZ7pYpHC7RfDTcJ89R9xR5lT3c5+dqYwxGfkPMD8GzB8iln0HMOMAUxkwjQDzNWCaAOYEwNQJ2+QAZglgBDB5gJkTsa6OgFkEmAaAqQmYLwDzjFr+G8CsBMwcwOSG950LmHzAvAWYbMB8AJj6R3k9KwBTuzReG2CaAWZ2WX+G/FfB/gFZBphhgEUG+LMBzlTLlhvgzjC+3QAvhvEQAzwbxsMM8LYBKoe3f2WAnx3lOWsaYIsB6oe3r7TrDm5fr9b/x3D77jFANwO8dJR1DzTASHV7mgG6RrR9ywA3hvFNBhgdxvVMWK3HAP+fAf4v8rUB9xvgnjL/HPmvWP8B5jrAvBTGnwOmZxifBZjtgGkOmErhvqVfuGx5+Nv9P8DcoNa1K/z/PMA8H/7GVwLM24AZkOK5DWCuC+OHAPNsGM8CzJlh/Ahg/niU+z8GTK+jvE6nDWCeBcxgdfslwFwZ/ntR3X+92q4/AmYGYO4BTLeC9y3mOQcCZqR33zjA9AdMB72fA8wwwIwI369OgFmiPoe3AXNGuN9uGd4/RG3Xv9Rn0xIw81NsyxDArA2PFWqExwS9ANMTMLMBUwswWYCZC5juMfdzn52h/8rN1M2efgBeMwaHAawXwQQEKQxjATwmggEIzuI2w1HSEIzBfBE8CeADALsBzEDwl2vB8vsB3C+CoQDuAPCwMRgHYBwAiOAGAO8C6CCCnwHYCuAuY7DHe6r6xmBnKb22DYge/iIqGmN2QaQngP4IRjleh8h9MGZY2GJU+H8+wlGWFEbAmNTzpKd2MYCJMGZLGttnz8xA5C0At0DkfgSpUONgzAveI5oA2JjmdpyOwtf0CoDfhnFzBO9DEwBVASyLWccGIL0cUypXrgXwpzD+d3g7P7w9xRisAgARzACQhyC1AghGDH9rDF5Nsc7zwn/Tw9tZANrDS1tAsC8ouHblnwBGiSAbQF1jMCG8fziAEVH3H9tLPT7GOGdP3wJwiwhsHzUGsX1UBI0QvA+fGQMjgoMi6GwM5oRNRhuDbwDMC9sW6AjgeQDnGQM9qlVgEIBOUnj+vo4Isow5Ikd7nDHYHG7LKAT7awPgTWOwW93fHwhSI1PcPybF83OfnQEyOWViLoI8oWNxHYBcAD1NkPe7HkD1oz3IGLxkDHoagwEIDmgXpWj2KoDv6DtEUBNB7tVzAH4N4EYEP3aphj4OhUNFQMm/tuoA9h7j+omOLkgj+BjGPIzgD0TdJ/aH/x8GIv/Y3n2Mz3gNCtMlAGA1gBbqdvPwvkIilyI4IMkC0BbGXA3gSojU9Na9F24fKkq/fAbAszDmFAC3IP73hv2yghFBfQBnA3hRBMsB/BzA1So1Yr9q7veLiQDO99MoClYN4HFj0C38184Y98KyCKU5sUBUXzxqHw1T/mwfNQZXA7gy3Kdqfh+9GkA9AMvC9zsPbt62fr/1+7oWwD4A3SNeSyUAp6n3u1mKg2HgyPe3uN5v/jZkgEw+IP4QQDUR/LDgDhF0CfN1PwXw3TCBPxfAAABTAGQD2GAMDopgIIBW4UN3Aqgd9UQiaBj+3xLBWaB/hbfbq2aXAljgPfTnAJ42JsxfDDrHN8ARnRoAFgL2AoCSfm0dAPsXM1HxEDkRIrpPdMPxzbgU2y8hkg3gTBTm3gPAlwDaQ6Q1RKoiOGAeox5TBcDdCM7gFvRJAKiM4AyuNh+wF9ACwFMAfgmRDuG6KkHk1nDZ5yjMV7wOQT8Fgn5ZsLO/8Sivjf2y4rkSwCvGoJUxyDMGLRCMEsTlxBd4CMEJmOdSLHsfwE1hfjJE0KxgP+WpFG4DEFzg/Zkx2A5ga7g/AYDrAUyIuj+M4/tiamMAXCOCaiJojeDM7RSEfVQErUVwRB8VwQGeUgkAACAASURBVPH00WsBnB++13kI/oC9Bke3DcCFAB4XwVkpln8AddGrCLpFrOdcEdQP86wvQ/BHzacALhNBTRHUAnB5eF/U/fxtyFAZe0BsDAyCL9AgCUqTzQXwOIB1CCo0zAIwE8HB5b3GYB2Cs7i9RDAbwA0ID2DDIY6JYWK7f1EdAIwUwTwEifo/MgbbwvufCB8zC8Hw1V0FD5CgRE0fU3h17DMIfghuRXhA7XkHwZXnpfHaBobPR1ScsgAMD0uSzUJwBfmvjmN9bwG4POaiussBfABjCs8qG3MIwZnp9xHsLP8DY+aqx/wIwHAEF7HNAlATIrMB5MOYbdCCi+eyw4vrAGNmIdhRvwaR+Qh2UAV/xN4J4Pvh674ehb8FvwIwAiL5ADYd5bX1RZhqRRXGtQh+s7WRSL/axF0ILjT7rb7TGHyAYD/yRfib/wZSH7DuBtBHBHMQnKl+JLz/RgBPhfuubmncPwzAX1NdVCeCy0WwCkHa0DsieD/cxrkILo6dB+A9BPvOwya4ON3po2HbAj8CMDxMK5wFoGb4GvPVvrfgfViAoJpEbRHkITgRNEktXwZguwhOTfHeOIzBegRVcp5L0f7HCPavs8JjgVuPWEFgCoLPdxaAkcZgqjGYhuD9mwJgMoAXjcH0mPu5z85QnLq5lEhQXuZlY3BuKTzXJwAuNQZbS/q5iMo1kZ8A2AljXizh5+kO4Kcw5voSfR6iCkYEPwGw0xiUbB8tQ9xnZ4aMPUNc0RiDtQBekHBijpISpln8nh2LKC1/gZt3WFJyADxYCs9DVNGUVh8tE9xnZw6eISYiIiKiROMZYiIiIiJKNB4QExEREVGi8YCYiIiIiBKNB8RERERElGhlPnVzTk6OycvLK+vNSJz8/PxNxpjc4lofP8fAzJnAoUPRy084Aejatfifl59nxcDP0RXXn0qqLxWXivJZHjx40Lm9bFnh7OTffPONjQ95H5ReVqlSpZQxAFSuXNnGJ5xQeEjStm3bIm5x8cqEz7Gs9isVUdznWeYHxHl5eZg6dWpZb0biiMjxzDB2BH6OAUk1Caty6BBQEm8TP8+KgZ+jK64/lVRfKi4V5bNcs2aNc3vw4ME23ru3cLbhTZs2Oe327dtn41q1atm4Zk13ItfatQvnG2nQoIGNR40aVcQtLl6Z8DmW1X6lIor7PMv8gJiIiIgy0yuvvOLcnjFjho2bNWtmY31gC7hnePXZ4vnz5zvtcnJybLxgwQIbT5kyxWnXp0+fY9lsomPGHGIiIiIiSjQeEBMRERFRovGAmIiIiIgSjTnERERElNLWrVud2x06dLCxMcbGBw4ccNpt27YtZaxzhgG3soTOSfYv5iMqaTxDTERERESJxgNiIiIiIko0pkwQERFRSps3b3Zu6/rCderUiXycrlFcvXr1lDHgpmRs2bLFxrNmzXLaXXbZZWluMVHR8AwxERERESUaD4iJiIiIKNGYMkFElCb/Sno9m9bf/vY3Z9mFF15o42uuuaZkN4yohOzfv9+5rStLHDp0KGXs01UmKlVyz8PVrVs3ZaxntyMqDTxDTERERESJxgNiIiIiIko0HhATERERUaIxh7iELF++3MZjx4618W233ZbW4/1cRT2bj4g4y/zbRHRsdIkoAHj11VdtPGLECBvrfg0AeXl5Nl60aFHk+plDTOWVnxt88OBBG+sSan4f0jnAut3hw4cj16dLuu3cubOIW0xUNDxDTERERESJxgNiIiIiIko0pkwcIz0MpMvH+MNKAwYMsPHKlStt/M477zjt3n777ZTPU7Vq1WLdPqKKbOnSpTbWQ7JZWVlOuwkTJtj4ueees7GfoqRvN2nSxMZ9+/aN3IYaNWo4t3W5qg0bNti4YcOGTjt/CJkok/gzy+myazrdwd/f6BnudMpfrVq1Iten1atX79g3lug48IiJiIiIiBKNB8RERERElGhMmSgheiipVatWNtYz9gBAx44dbTxw4EAbX3HFFU47PVTrD81qTJOgikSnQjz11FM29tMOokybNs25rftfbm6ujf1hYa1BgwY29mftqly5so3r16/vLLvsssvS2l69DqJM07hxY+d2tWrVbNysWTMbz5s3z2k3aNAgG8+fP9/GO3bscNrplCRdqaJt27ZF3GKiouHRExERERElGg+IiYiIiCjReEBMRERERInGHOJiosvKAEDt2rVtrMvP+GWgJk6caOO1a9fa+LXXXnPa6dzHli1bOst07vENN9xg47PPPjutbSfKVDp/96abbrKxn5P71ltv2XjdunU2rlu3rtNO5yXqXPxdu3Y57XSfjeu/ms4ZBoBLLrkksi1ReeHnxuuZUfWyjRs3Ou3OO+88G+vSan6pUX19jF6HzvEnKg08Q0xEREREicYDYiIiIiJKNKZMlJCvvvrKxo0aNbJxdna2007f1sPAfnknPfTrz+wzZswYG8+ePdvG+fn5x7rZRBlF94/evXtHtrvjjjtsrEs3vffee067sWPH2nj58uU21ilOgFuGTZeZ0mlNAHDrrbfa+Pzzz4/cPqLyyi+7pkuKav5srbqcmp6NUc+mCrizQuq4RYsWx76xRMeBZ4iJiIiIKNF4QExEREREicYDYiIiIiJKNOYQHyNdciaOzpPSOYibNm1y2ul8YJ2D5edZ6eld/RJvOkdZ508SVVQ6JxFw+4cup3b55Zc77c4880wbP/fcczbWOf+A2/90n/LLuPXr1+9YNhtA/LYTZZpevXo5t/V+SvcNP4e4VatWNtblCnWeMOBO5Vy1alUbt2nTpohbTFQ0PENMRERERInGA2IiIiIiSjSmTByjdFMmdNkmPYS7atWqyHZ6yMkvraaHcOO2YevWrWltH1F5FpdmoFMS/HZ6Zi1dJu3ll1922q1fvz7lups3b+7cjpu5Lm47iMqLE0880bmty67pGR79dL2mTZvaWJc13Ldvn9NO7+tq1apl4ypVqhRxi4mKhmeIiYiIiCjReEBMRERERInGlImj8FMXotIVpkyZ4tzWw0IdO3a08RdffOG00ykTOi3CHy7SM9fpK3EBN9XCn+GOKBP4lRW04k4nSDdVQc98N2HCBGdZVJpTzZo1094OpklQReDv8xo0aGBjvZ/z2+m+0qxZs8h2ml/Fhag08QwxERERESUaD4iJiIiIKNF4QExEREREicYc4pDOFdY5TnH5TnoWrNGjRzvL+vbta2Od16tn5QGAOnXqpFy3/7w6H9Ffpmeu02XXtm3b5rRjfhYdi6i836LkxpZmPm1Rnssvp9a4cWMb63JSDRs2LPqGhfzti8uvJso0ega5DRs22NifQVVr27atjVu2bOks09//Dh06FMcmEhUJzxATERERUaLxgJiIiIiIEi1RKRNRaRGpbhd44403nNvXXnutjXW5s1tvvdVpp2e6+uijj2ycm5vrtNOz/uiho7jt80vBRQ0R5+fnO7fPOeeclO2IUimvZcPitlunP+jSatWqVXPaLV682Ma6BOKMGTPS3o4VK1bYeObMmTYeO3as046pTFSeNGrUyMY6ZSIu9cdPSdL0frQ4UpKIiopniImIiIgo0XhATERERESJVi5TJvyUAS2uKkTcsiVLltj43HPPtfHy5cuddrp6RJ8+fWw8fvx4p93OnTtt3KpVq8ht2LNnj411NQo9a53/OH8deqhKD2eNGTPGaceUCcoE/tBqcaRmpDs7nT/LY4EePXo4t++77z4bn3322TZet26d0+69996z8bRp05xlevZKfWV+06ZNnXZnnnmmjZ944onIbSfKBFH7olq1ah3zYwC3T+oZ7YhKG88QExEREVGi8YCYiIiIiBKNB8RERERElGgZlUPs581qlSoVHrvH5QLHGTlypI3vueceZ5kukdS7d28bX3TRRU67uXPn2vjVV1+1cb169Zx2WVlZNta5wT5d0km/fv8xBw4ciFzHvn37bKzLSo0bNy7yMURHU5CXGzezWqbMWpfuOqPa6Tx/ALjmmmtsvGXLFhvrGewAYOjQoTbu2LGjs6xr16429vOGtQEDBsRsMVFm0fspvV/ySxdqcbPY6f157dq1j3PriIqOZ4iJiIiIKNF4QExEREREiZZRKRM6LaKo9AxTt99+u7Ns0qRJNtYl0wDgggsusPFXX31lY51mAbjDQrrEmZ/uodMY9BCzXzIuavY8v4TN9u3bU67Pf249NLVgwQIQFbeotIO4marSnT3Ob6dLMsWtP93niqL7F+CWTdy2bZuNdfk0APjNb35jY/06AODhhx+2sR5a1mUdicqbXbt22Vh/r+PSHXSqkU4T9NcRl3ZBVNJ4hpiIiIiIEo0HxERERESUaBmVMjFnzhzn9iuvvGLj3bt323jmzJlOuw0bNthYD7n4V4TrihGrV692lukZp/QwbZMmTZx2hw4dsrEewtX3A24qhB7C9YdzdbqDTpnQw7SAO6zkX7Grn1tvu5+e4c+6R1QUUVUm0k1V8NMTsrOzI9vq731R0ifi6JSiRx55xFlWvXp1G99///02Pumkk9Jev640o9Mp9Mx3ROWNTpnQ+6+4lImaNWva2J8t0t93EpUVniEmIiIiokTjATERERERJRoPiImIiIgo0co8h3jbtm0YNWoUAODHP/6xs0yXPtI5SH4OrV6mc/X07HOAW07NX4fOf9Ll3/bs2eO00zmNOkfXz9fVuVVRM/sAbt6lLkejy7YBbs5kujP6+caOHRu5jMhX8N30v7N+DmABnVsIuNcE6Hzae++912k3f/58G0+ePNlZ1rBhw9htO1YffvihjX/3u9/ZuF+/fk67X/7ylykfn+57Abi/KZyBiyoKvV+Om4VV+/rrr23s71MPHjxoY//aGaLSxDPERERERJRoPCAmIiIiokQr85SJGjVqoEuXLgCAb33rW86yefPm2ViXXdNDLACwdetWG+tUiM2bNzvt9DCrX7ZJpyjo8mfFzU+t0OWd9PbFpVb4KRN62DZuCNefSYsoHXHfqRdffNHGfjlE3f90abVbb73VaTd69Ggb69kfAWD8+PE2Lkq5Mj07JeCmSZx//vk29tO1NP1b4b8XUSXogOC3rQBLS1FFUadOHRsvWbLExv4+S9NpEn7KhE7BKGoqFFFx4BliIiIiIko0HhATERERUaKVecpEtWrV0K5dOwDASy+9FNlOD2mOGzfOWda6dWsb6yGXzp07O+30UI2e0Q5whzR1SkK61SN8+nE6BUNXkgDcqhBxqRr6cf469LCtThnxh5/8VBOi4+XPLqnpmSK3bNli42HDhjntdKpU//79nWV/+MMfbNytWzcb169f32mn+4BO3Xj44Yeddtddd52Nb7jhhsht14o6jJuXl2djnfJFVJ7pfZbep8RVONKpgf5+Tu97/ZlhiUoTzxATERERUaLxgJiIiIiIEo0HxERERESUaGWeQ6xt377dua1LNT399NM27t69u9POL60URecN65wmwM351cv8vCg/p/ho9wNurrGfx5vu+nSelV8yTpe70dvr5zg3a9YschuJtB07dthcfT27G+CWU9N9z5+1ys/zLaBz/gHg7bfftrH/3e7Ro4eNdQm2U045xWn3wQcf2FjnDT/zzDNOu8GDB6fcpjhxpdV039Nl1gDmDVPFpEuU6u9/ixYtIh+jc4P9WWL1vi5qZkqi0sAzxERERESUaDwgJiIiIqJEy6iUCZ0i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u6ysrJSxTw+X+jPLNWjQwMZ79+61cbVq1SK3XZeJ88u46dQIXRZu586dTrsHH3zQxiNGjHCWvfnmmzZmmgRRenQf3b9/v7OsRo0aNl6xorCO+0UXXeS00/102LBhzrKzzjor5fPGlY0kIqKywaMnIiIiIko0HhATERERUaJldMpE1PD/Qw895Nxev369jVu2bGljv/KDP1Sp6WFLPXyq0ycAIDc318YNGzaM3NZdu3bZeNWqVTb2Uyb0Nul1+O3q1Klj41mzZjnLbrnlFhu/8MILIKKj0/1Np0gAwJw5c2ysZ5D0f0N0StWQIUOcZYsXL7axrlQhIkXbYCIiKjE8Q0xEREREicYDYiIiIiJKNB4QExEREVGiZXQOcZRRo0Y5t+vWrWtjPQOdnxeoc/d0ySX/cT169LBx48aNnXbLli2zsc4L9Eu8aT179rSxzicGgM2bN9u4du3aNjbGOO30bZ1PDABTp0618aFDh2zsl4wjShqdyw9El1v81a9+5dz+xz/+YePq1auntf5nn33WWaZ/H9gviYgyG88QExEREVGi8YCYiIiIiBKt3IzdPfroozbevn27s0zPHrdlyxYb+0OdOmVi9+7dzrJLLrnExrq00pgxY5x2p556qo11moQuwQYA+fn5Nm7UqJGNzznnHKfdhAkTbKxfV7169Zx2ehY7Pbud/7jf//73Nr733ntBVBH5KUVRKQlxM1LeeeedNn7uueecZa1atbJxixYtbDx37lyn3cCBA2181VVXRT6X3iZ/21mGjYio7PEMMRERERElGg+IiYiIiCjRyk3KxPPPP29jPxVCz0inq0f4aRF69jd/Hbraw8cff2xjfzhz5cqVNtapC/4MVnpGu5kzZ9o4OzvbadehQwcbf/7555Hbp6tT+MPAuu3f//53GzNlgioS3bf9mSF1RQft008/dW5/97vftXGbNm1srPshAKxbt87Gup/37dvXaTdy5MjI7dW/CXomTKZIEBW6+eabbaz3m4899ljkY3TaUVx/8vfLuh8S+XiGmIiIiIgSjQfERERERJRoPCAmIiIiokTL6BzivXv32ljnzfr5tVElybZt2+a004876aSTnGWLFy+28aBBg2ysSy4BwM6dO23cpEkTG/u5ir169bJxv379bKzzhAE3/6lLly42njJlitNO50z6+ZP6dekcqQULFjjt/NdMlAnSzQf0v/fa2rVrbfzQQw/Z+JVXXol8TPPmzW3s5xAvXLjQxv3797exX4ZR06XfgOhSa/qaB+DIMopEmeTgwYPO7ah8fV+6/XrTpk02Hj16tI1/8IMfOO3atm1rY309gZ8XrLfXX6ZzivXvCfP6CeAZYiIiIiJKOB4QExEREVGiZXTKxF/+8hcb6zJIeuY3wB3u0MOU+/fvd9rpYRZ/Zjk9zKJTNfRwDuCWctPt/GEkvb5ly5alfAwA9OzZ08azZs2ycffu3Z12OqXDH5rVqSF6+9544w2n3QMPPACiTKP7b1zawezZs208ZMgQp92SJUtSrtv/rdD9UqcULVq0yGk3YsQIG1955ZVRm+7wh2d1X69Ro4aNq1Wrltb6iDKBv29LNxUiapmfxjRnzhwb16lTx8ZxJdLilqWb0qFx9kgCeIaYiIiIiBKOB8RERERElGg8ICYiIiKiRMvoHOKLL77Yxnr6440bNzrt3n//fRvrXKCmTZs67Xbt2mXjyZMnO8t0vl+nTp1srHOXATfHUeco+zlHOiexffv2NtYl4gC3DNuMGTNsrPOOAeCuu+6y8X/+8x9nmZ6iWec79u7dG0SZTvfZuNJqOgd++vTpzrJWrVrZWPfF7du3O+30dQQ6X9H/TWnduvXRNvsI/m+AzhvW/vSnPzm3ly5deszPRVRWdH9Nt+/eeeedNtb7a8AtSzpx4kQb6+sHfHHTuI8aNcrGTzzxhLNMT91+zz332Njvu35OMSUDzxATERERUaLxgJiIiIiIEi2jUyZ0qsHw4cOP+fH+cIku4+aXPtKly3T6RIMGDZx2Ou1Cl3fxh3f0jDhxqRX6ti4ls2fPHqfd66+/njImKu90X/H70Y4dO2ycn59v43bt2jntdJ9dtWqVjfVsdIDbr3Sf9/u5nmmyqMOnL7/8so31b8+kSZOcdumWdSMqLXEpCXGpEdrdd99t4xdeeMHG119/vdOuR48eNtYpTjp9AnDTHeK24bbbbrOxnwql998/+tGPbOzPfkvJxDPERERERJRoPCAmIiIiokTL6JSJ46VnpfLpISEAqFevno1btmxpYz+1QqdJ6GEbf+YcvQ697MCBA047PbOcXndRZtsB3NfsDz9z9h3KRHEpE//85z9trNMi6tev77TT/eqxxx6z8dChQyOfV/exnTt3Ost0hYg+ffrYeMqUKU67f/zjHzb+wQ9+4CzT/U3PjNmiRQun3YMPPmhjf3ZJIq0gfSfd33I/3Scq/aeoaREvvfSSjX/5y186y37605/a+LXXXrOxX2lp6tSpNtZ9/PHHH49sN3DgQBvr1AwAqFmzpo3PO+88Z5n+nfjFL35hY7/yC/eVycQzxERERESUaDwgJiIiIqJE4wExERERESVahcgh1nmzOi+wbt26Tru4vCid1zR37lwb6/xG/7Yu4eKXbdF5w1lZWTb2c5d1SbaTTz45cvs0Pze6OHKPicpKXL8899xzbfz888/beP369U67Ll262Dgub1jT/cifVU7fXrNmjY3btm3rtNu0aZONs7OznWW5ubk21uWk/OsN9LYTxSnIbY3LDdaxv78pyv7hiiuucG7r7/W8efNs7Jc5/fTTT22s+67e5wHujJGNGze2sT/TrC67qGej86/z6dy5s431NTqAe42Cfz0AEc8QExEREVGi8YCYiIiIiBKtQqRMRJVI0UM7gDs06z9GDyXpGazi2ulhVX8IS6dW6GHVqlWrOu30cI8/lBqlqDNnEWUiv9Sapmer1H3R75dffPGFjU8//fSU98cZPXq0c/vyyy+3sS7V5KdQ6bQsP+1C00O3P/nJT9LaJiJfVNm1qH2gv0/RMzU++eSTNh47dmzk4/zSZXr2t7vuusvGCxYscNr997//tbFOJ/Jnhdy6dauNly9fbuPTTjvNaaf3o506dbKx/9r1OvwSh19//bWNa9WqBSKNZ4iJiIiIKNF4QExEREREiVYhUiaiUgj07HNA+rPv6LQIfzgm6mpef916GFi307PoAO4QrB6ajUuL4Cw6VN4cOnTIxv6V77rvxKVP6D6hh34BoFGjRjaeNGmSjb///e877fTMcrpKzGWXXea00+kPP//5z2188803O+1++MMf2lhfVQ+41WV0atSQIUNAVBRRv/1636GrJK1YscJp97///c/GkydPtrGfXqjTIr766itnmU55ePnll1PeD7gzNy5ZssTGut8BQNeuXW2sK1D4FSJ27NhhY121xa/wpNMk/N8a/f7p98afQdZPbaRk4BliIiIiIko0HhATERERUaLxgJiIiIiIEq1C5BBH5VX5ZZB0PlG6pcvicpA0f33+4wr4uUq6vE1UfrKPOcSUifySZPo7HJcbnC69Pn+2K327ZcuWNh42bJjTTpdTu/LKK23sz/44e/Zs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57VPgwYNKpU99dRTyf7GN76R7Dwz1Z577plsn2Hr8ssvL9W79957k+3Dxayyyiqletdff32b9llnnVV5XiG6IhMnTixte738Ouusk+wXXnihVM9rft97771SmfdtrwfOdY1e8+g1ynnYtd12263NNl177bWlel7D78Oz5drlWbNmJTvXPG633XYI0R2p0xD/7W9/S7bP1Jjj9frex+vCp22zzTbJHjNmTKnMa4j98wT5MwlCLC6aIRZCCCGEEI1GA2IhhBBCCNFouqVkoi7Mig+Zli/N+JBJfjkHytnk6kLJ7LPPPsn2S7i/+93vSvX88o4Pv5Rn/fFt8pm48iw9kkyIrs748eNL2/677WVOueTJZ6rKJQ7ed3w9vwQLH5QytJAv93qJg5dn5H75+OOPJ3uttdZKts9oCeVrefTRR0tlkkyI7kruNx4fovSAAw6orFfVT9f13+uvv36y89Co7W2fEIuLZoiFEEIIIUSj0YBYCCGEEEI0mm4pmci58sorkz179uxkr7zyyqV6XiZRF6nCP30+YsSIUj3/dKtfft1///1L9V5//fVk++XYfGnXZ+3xWbr8sQEeeOCBZGspVnRFnnvuudJ2v379ku0jSzz//POlehtttFHlMb3sycsn8iVTX8/7lJdZ5OeeOnVqsvPMkP4e4KNnrLrqqqV6vk3Tp0+vuAohuhftlSRsttlmlWXeJ31/W3fsTTfdNNkvv/xyu44tREehb5UQQgghhGg0GhALIYQQQohGowGxEEIIIYRoND1CQ/zb3/422T4TXK4TzkMrVZX5sGtz5swp1fMaQq8nznWRvXv3bvPYXnOYb3sdc17vqquuSrY0xKKr4LM/eu0ulHW4t956a7Lnzp1bque183X4jFR1mer8swO51nD11VdPtvdLr/mHsv+uttpqyc51jUOGDEm2z3YJ5ecAco2yEJ1N3j966kKj+XCjdfg+rL0a4rzf80yePDnZPkNe/lyOQrKJxUUzxEIIIYQQotFoQCyEEEIIIRpNj5BM+GVMv+SSZ7NaccUVk50v0/plFv+6PGxTlawhX6bx9by0Il9ueuutt9q8jvy8PjuQEF0FH2otlydUSQ3ybHTe33I/qvLLurBLPgNdXs9v+2N7OQaU7xX/+Mc/kp37pV+6zcM8+sx1u+22W2V7hehscjmh9408BGgujWrB+x1UywFzfDhU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euJcg1SlhcrP68NC+dfk2mV//FzvKER3Is/W6LdPOumkUtkGG2yQbO8feWbI448/PtkvvvhisvMQb8OHD0/2Wmutlezrr7++VM8/i3DooYe2cRVCNJM8DFsLM2bMKG1XhTjzIUQBNtlkk2R7v5s0aVKp3oorrphs3x/mOuHlllsu2T40KpT7W58VU1nrBGiGWAghhBBCNBwNiIUQQgghRKPpEZIJv0Tav3//ZOdZ4fwyS56Bzi8DVdk5fgnXL9NAeWkmP1dVmzx51h+/LJSHt/HSkDy7jxBdjTx7nJcRffvb3y6V+WXTr371q8n+85//XKp31llnJXu//fZLts/+CLDrrrsme+zYscnOl3dz6UYLdfcNIZpAVZ918803l7a9/GHDDTdM9uDBg0v1fD/6+OOPJzvP1rrmmmsm28szcvlU3ndWtclnnZRkQoBmiIUQQgghRMPRgFgIIYQQQjSaHiGZqMpAN3fu3FK91VdfPdl10SPqqKqXL6X6ZWC/rFp3Hn8dedv9cpHPxAXlZeWtttqq8vhCdAXqskLl0qNp06Yl+9VXX0321VdfXar3y1/+MtlTp05N9mmnnVaqt8suuyT74IMPTna+zPqxj32szfbVZZoUoieS91lV/vvoo4+Wtn0GOd8/+n4O4MYbb0z2gAEDkp1HU/LypzpZo8/qmrfdy7W81DK/n/h7g2gOursLIYQQQohGowGxEEIIIYRoNBoQCyGEEEKIRtMjNMQ+q5vX+M2ePbtUz2sQhw0bVip788032zxGHb5enS7SUxdO7Yknnkh2Hj7Na6PzsFXSEIueQr9+/Urb6667bptlhx12WKneDTfckOzPfe5zye7bt2+png+75O8BuS6/6h7QXj8XoqfQXg2x1wxD2V+9rjfvl/3xfDa6PBTiG2+8kWwfUjUPu+afv8lDr/pnFHwouN/97neletIQNxPNEAshhBBCiEajAbEQQgghhGg03VIy8cwzz5S2vdzBk4dj6dOnT7J9djcoyxDqlkWrMlPVhVPzx86XYl977bVk77vvvsl+6KGHSvX80k/evnnz5lWeW4jujPePE044IdleFgEwatSoZN95553J9pkrASZOnJjsU089NdlediWEaKW9IUmfe+650raXAz744IOVr/PZI71UMJc7zJo1K9ledvH000+X6nl5xqqrrloq8+HfvCTjtttuK9Wb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",
            "text/plain": [
              "<Figure size 864x720 with 30 Axes>"
            ]
          },
          "metadata": {},
          "output_type": "display_data"
        }
      ],
      "source": [
        "# Plot the first X test images, their predicted label, and the true label\n",
        "# Color correct predictions in blue, incorrect predictions in red\n",
        "num_rows = 5\n",
        "num_cols = 3\n",
        "num_images = num_rows*num_cols\n",
        "plt.figure(figsize=(2*2*num_cols, 2*num_rows))\n",
        "for i in range(num_images):\n",
        "  plt.subplot(num_rows, 2*num_cols, 2*i+1)\n",
        "  plot_image(i, predictions, test_labels, test_images)\n",
        "  plt.subplot(num_rows, 2*num_cols, 2*i+2)\n",
        "  plot_value_array(i, predictions, test_labels)"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "V8fh0ar08SvL"
      },
      "source": [
        "### Make a prediction using an image from the test set"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 21,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "8b2sGFcC8QcH",
        "outputId": "8413036f-535b-4bff-ba6d-ca36e7960f5c"
      },
      "outputs": [
        {
          "name": "stdout",
          "output_type": "stream",
          "text": [
            "(28, 28, 1)\n"
          ]
        }
      ],
      "source": [
        "# Grab an image from the test dataset\n",
        "img = test_images[0]\n",
        "\n",
        "print(img.shape)"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 22,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "y3y8Bo9g8XGD",
        "outputId": "f200d9a6-7240-4098-8e04-f150514b0b1c"
      },
      "outputs": [
        {
          "name": "stdout",
          "output_type": "stream",
          "text": [
            "(1, 28, 28, 1)\n"
          ]
        }
      ],
      "source": [
        "# Add the image to a batch where it's the only member.\n",
        "img = np.array([img])\n",
        "\n",
        "print(img.shape)"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 23,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "UjxuEz2D8Y2a",
        "outputId": "f22342db-56ab-44f6-efe5-bfc659d171e0"
      },
      "outputs": [
        {
          "name": "stdout",
          "output_type": "stream",
          "text": [
            "[[3.8163607e-06 7.6481086e-07 3.1365922e-03 9.4044872e-06 9.3140233e-01\n",
            "  2.0095563e-08 6.5446995e-02 2.0135031e-09 1.0240740e-07 2.5441089e-08]]\n"
          ]
        }
      ],
      "source": [
        "predictions_single = model.predict(img)\n",
        "\n",
        "print(predictions_single)"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 24,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 300
        },
        "id": "tuXPip0c8bBF",
        "outputId": "6029210d-45cd-4dc6-804c-a1961a22057a"
      },
      "outputs": [
        {
          "data": {
            "image/png": "iVBORw0KGgoAAAANSUhEUgAAAWAAAAEbCAYAAADkhF5OAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADh0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uMy4yLjIsIGh0dHA6Ly9tYXRwbG90bGliLm9yZy+WH4yJAAAdmElEQVR4nO3deZxddXnH8c8zCSEBDVuCiSCEJYRNRJAiEhYTwi5BSFiEgmIiWyohKElRNgUMtLQVREEgArHUSFBQVEQsKChWAUWpuOFS1BZBq7SgKPD0j+e5zMntJMzMPef+huH7fr3ymnvv3MzvnHPP+Z7fds41d0dERLqvp/QCiIi8VCmARUQKUQCLiBSiABYRKUQBLCJSiAJYRKSQkQN587hx43zSpEkNLYqIyPB03333Pe7u49tfH1AAT5o0iXvvvbe+pRIReQkws1/09bq6IEREClEAi4gUogAWESlEASwiUogCWESkEAWwiEghCmARkUIUwCIihSiARUQKUQCLiBSiABYRKUQBLCJSiAJYRKQQBbA0YsIEMGv234QJpddSpDMKYGnEo48OjzJEmqQAFhEpRAEsIlKIAlhEpBAFsIhIIQpgEZFCFMAiIoUogEVEClEAi4gUogAWESlEASwiUogCWESkEAWwiEghCmARkUIUwCIihSiARUQKUQCLiBSiABYRKUQBLCJSiAJYRKQQBbCISCEKYBGRQhTAIiKFKIBFRApRAIuIFKIAFhEpRAEsIlKIAlhEpBAFsIhIIQpgEZFCFMAiIoUogEVEClEAi4gUogAWESlEASwiUogCWESkEAWwiEghCmARkUIUwCIihSiARUQKUQCLiBSiABYRKUQBLCJSiAJYRKQQBbCISCEKYBGRQhTAIiKFKIBFRApRAIuIFKIAFhEpRAEsIlKIAlhEpBAFsIhIIQpgEZFCFMAiIoUogEVEClEAi4gUogAWESlEASwiUogCWESkEAWwiEghCmARkUIUwCIihSiARUQKUQCLiBSiABYRKUQBLCJSiAJYRKQQBbCISCEKYBGRQhTAIiKFKIBFRApRAIuIFKIAFhEpRAEsIlKIAlhEpBAFsIhIIQpgEZFCFMAiIoUogEVEClEAi4gUogAWESlEASwiUogCWESkEAWwiEghCmARkUIUwCIihSiARUQKUQCLiBSiABYRKUQBLCJSiAJYRKQQBbCISCEKYBGRQhTAIiKFKIBFRApRAIuIFKIAFhEpRAEsIlKIAlhEpBAFsIhIIQpgEZFCFMAiIoUogEVEClEAi4gUogAWESlEASwiUogCWESkEAWwiEghCmARkUIUwCIihSiARUQKUQCLiBSiABYRKUQBLCJSiAJYRKQQBbCISCEKYBGRQhTAIiKFKIBFRApRAIuIFKIAFhEpRAEsIlKIAlhEpBAFsIhIIQpgEZFCFMAiIoUogEVEClEAi4gUogAWESlEASwiUogCWESkEAWwiEghCmARkUIUwCIihSiARUQKUQCLiBSiABYRKUQBLCJSiAJYRKQQBbCISCEKYBGRQhTAIiKFKIBFRApRAIuIFKIAFhEpRAEsIlKIAlhEpBAFsIhIIQpgEZFCFMAiIoUogEVEClEAi4gUogAWESlEASwiUogCWESkEAWwiEghCmARkUIUwCIihSiARUQKUQCLiBSiABYRKUQBLCJSiAJYRKQQBbCISCEKYBGRQhTAIiKFKIBFRApRAIuIFKIAFhEpRAEsIlKIAlhEpBAFsIhIIQpgEZFCFMAiIoUogEVEClEAi4gUogAWESlEASwiUogCWESkEAWwiEghCmARkUIUwCIihSiARUQKUQCLiBSiABYRKUQBLCJSyMjSCyAynCxatKjxMhYvXtx4GdIdqgGLiBSiABYRKUQBLCJSiAJYRKQQBbCISCEKYBGRQhTAIiKFKIBFRApRAIuIFKIAFhEpRAEsIlKIAlhEpBDdjKdhujmLiKyMuXv/32z2GPCL5hZnBeOAx7tUlsoeGuWrbJU9XMve2N3Ht784oADuJjO7191fp7JfOuWrbJX9Uii7Sn3AIiKFKIBFRAoZygH8UZX9kitfZavsl0LZzxuyfcAiIsPdUK4Bi4gMawpgEZFCFMCDYGZWehmkO8zsZfq8BcDMevJnbfuDAniAzMw8O87NbB8z26DEMgzHsrK8dSuPp3Sz7D6WZTKwFNi+S+UNuStTq5+/mY3qRjlDkZmtA4zNp7XtD8MmgFsfoJmNMbM1miqnEr5vBM4C/qepsvrSdgI4yMzW7lJZ08xs66bKyjJ6gGlmdomZnQAsNLOxL/T/muLuPwZ+Biwys+2aLMvM1gJ2ysczmt7W/dH2+b8NOLJVC6zr7+fPycAxTQZ8DXYj9sdzgaW1tYzcfdj8Aw4GbgO+Dvw1sGZD5RwK/Bo4KJ+PKrCuBwD/BozrQlnzgW8Bm3Rp3b4N/A54VT5frcvb1oCeyvPFwI3Adg2WuQWwELgZ+EFT++4gl20X4Fbg5XVu4/y5J/Ap4JvAYcDqpdd3Fcv8ZeD3wO51/c3hVAPeClgAnAmcTwTwUfm7js5Uffz/zwC/Bd4J4O5/NrMRnZQxwOXZFbga+IC7P25mqzdY1jRiO05195+Z2WvNbK+ay6g2c1cndvS7gQ+Y2Uh3/0ud5b3Qsnh4zszWA3D3RcD3gXPrrgm31t3dfwRsAPwV8Eng6TrLGSwz2wG4AngUeLKuv+vubma7AZcDS4AHgN2Bw4dKTbiP4/4S4rM52sy2rKWMTPYXNTPbHLgAGOHuh+ZruwDLgCPd/Wsd/O0V+nyBZ4EHgceA7wD3u/ux+fsR7v5sRyvzAsuQz9ck1m2iu+9YZ9l9lDUZWESc+Z8lmsl/BK5z90/UWV6eRJ9w91/l838BRrr7bDPbk6gdfbHTMvu5XPOAnYFHgKvd/WEzOwfYhjjx3V9DGdV1fzvwRuLkM5loAVzv7r82s3HAb70LB2v755+vzQWOJSo436prOczsdKKmf3aeeN8OvBm4CvhUN0+8fSxb9bM5lLhz5JPufouZ/R0wETgVOAT4k7tfO5hyXrQ14Laz08+JZuva2X+2hrvfA/wLcdejQat8CO8igmhfYmBmMrADsK2Z3ZTvbTR8zWwvMzsQWAc4GnjAzG5uhW+ntfC2sk40s0OAp4hQeCWwnOjm+So13cq0Ut6pRE3rOjO7Ivsa3wGMMLP7gX8EflJHmS8kA+cw4G/z5wVmtpu7n0Psa6d22uows7GVdZ8KzAROcvePEV1LGwKzzOwMYqyhsVZOVWWZ5pjZmbnfLwVuIFqXr6uxH/iHwOvNbGt3f9rdPwyMAKYCtdQwB6uyHd4JnA68BjjOzK5x93cDvyH2yXcT2TPogl50/+ituU8FjqS3L/ZdxCWGi4AZwC+JpnOn5W0OfDofn0/0062ez1cD7iICyhpc59OArwAfAu4k+uVeBlyZz3tqLGse0ee7eR+/Oyp3uC1rLO9o4K58fAHR1F1S+f0sYFKD23YnIgBXz236d8AEoovpdqIP+DZgt3x/R/3uwGZEuI8G1gZuAu4DXl95zwFE4N1Dg33PK1m+U3K9pwHfBRbk6wtzX99hEH+zdczuCEwHNsrtfQHwHqLrZUruyzcB7+3mOq9kmUcDn24dB8Ao4J+Bhfl8S2D9jsoovZIdbJx9gO9lIH6ZaLKQB823Mpj2zdcGFE7tQQpsDFwHfBC4pRK+h9QZfKtYni0q67cQ+ALReukhpsZcRg5Y1VDWuDz4tskwOoJoau1JNMm/DLy6wzLat+92eUCeTJzc1gIeJgZnGh+AA95CDAIdkM9HZUh+sfKehzMs1qihvE0yeLcnTu6t/WsBsFnlfT10YTCOFQcce4ianREVms9lUI7I388b6L5WCd/9gB8B7yX6lF9HtCIXAt8gav5bESfci1pldutfH/vlGkSl54DKa/sB/1Bbmd1cwTp3GKJZdHjltVuBD+fjs4FLgTcM9ACufgjA4blDjCJqnvcDG+bv5hC1lo7OgP1YnvHAy4kBgCXA51vrRJwAxrbvOB3udCNzXZcRI/9XAdcTJ7bVgLU7XJ/q9l0LGFv5TK8D9svn78+DcnyT+1Hl8fnEwN/sfL4RMRvh9cD+xIl3gxrX/eVZ5tXAJKL2t5Q42U1ucp9axfLtQ5wYlhMn4eXkDB/gBGBGB397G6LltFmW82hu3+mV/Xyd/N33gW27vO7Vz2YXotIzluhyfBh4Q/5uLlFJGN3Jcfd8WSU+6EFsnFHAlHw8CVg/A/awyns2Bq7Nx6sB/0CcRQdVYyFqY98DNs3nM4im6B1ETehBYJuG13t74EJg3Qzgu8gaEvA2onk4oaadbibRnTMly51FTjsDjs+DcWSN6/Yuoqn5HaJbY0OiP+0y4H0ZeLXU6vuxLPOI2vb1RLfVm/P1E4CvESfejgKhr4MVeBXR/L489+stcpucXOe2XsUy7UBvt8rLgW/k4+kZOq2T0bHAQ61joZ9/ezOigjCz8toWwK7Avfl8IfBnYFo+H0uMAzR6XL3Acv8N0YK+lugO2Zs4Af8K+DBxcti6tvJKregANsh6xPSUuRlG3wHWJKaZ/WfrwyJGkO8ma0xETa7ftae2MHo1UbvdIJ/vQfSHtfoKZ1FpKja47jvlwT+FGAS4guiTugz497p2VOBEYu708cBfgF1b2wR4K3Ei6minI/r+/oqoYU0jmvxjiUGuK7KcnYn+x892GngDWK7N8rPeKJ8fmQfgrHy+Pp3281WCi5hT/TFiYO0VRJfPWfmZbkp0SbyyC+s9Mj/3f6183q3PZHTu4z8Frsnt0+99jQjaB4GLc786ofK7OfS2VPfMkKv2fXd1znfbck/OdZ1AdD/slcff5DwGt6bmSkGRFR3ABhlF1AYOJZrFTwNnV35/CnFmvoQ4M7X68DrqlyUC/lKiZnI50Q90I5Uad8PrPbG1DnnALssDZtPcKWbTwUURrHiyWZ8I9bWA44g+3hGV3/09nYfvvhlqxxA13cOBpZXf702lhtXkQcj/73IZRcyWmUpv1865wP+SYwgdlrceMdr/XuIEdBcx6HghMZ98Yr5nMdFqa7zm27Zs7yBOeNOJ6XVUPv/JxOByv09AGVLfBt6Uz48mgn77fL4bMZf2g0QL7vV9fS5dWv+eatl5fH2u7T3nAHMaW4Zur/QgNtLJxGjwFKLpfz4xMNQ6WHYFtgVe2+kHSfQ/fSUfv4noS94un58NXNj0zkLUAq8kZnOMzcC6kJpq3G3h+xaixrUwy7y1sl1PI2poHQUC0Xr4MbBT5bXtiSbezpXXlpAzVpravm3rPoneFs5FuY+1ulxmZiht2GF5B+a2nUa03L4IHJi/G58H903EBRjr0p2rGttPQGOBk4ja73NEP/yXidH+yxngQBhxInuu8vy7xKDxd/IzHkFUIs4m+/tL/asE70b09nXfRHZl5vPzgfMaW4aSG6C/Gyk/wBPz+SnAPxH9MlOJfrpB1Xj72Bl7iA72G9pefws1T73qaxmIvuvRxAnlYmLq00nEVUIfqrnc2USXzeZ5oD1I74DY7DxwJtVQzgLglHw8Mn+uRZxMFxN9wW8l+hw7CrwBbOcFRBfOZ7P8MURT++NEa+MB+piCN8DyDsy/0+rK2AC4F7iy8p71iClvnxho0NWwDaYTlZdX5PMTie6A44iT/iQGedInZgr8lBjIOytfG0XMgDhtZcvUrX+57nvl41Pzc/p4HnNrE63dLxIn5QfI8adGlqXbK9+PjTOavOac3n65zYla4PrEGftU4CPEZOgDaihzC3K6D3GGXgZ8Pp9vlc87mnrVj2U4MXeCK4E98rVpRF/3j4kulnVqKmsnoil8cj5fPw+WazIM7qWmQSeiK+e81mv0NvvWAc4gZgFcTZcGXogWxseJqWBbEn1+rXmdr83t3VFrg+hDvIOs9Vf2rd2Im/vMq7y3KzXftuWbR9R4z8x9q3WcnZD7xa41lDEdeIYVZ5q8vT2AS/wj+vmfI2b2fDSP8W1zP7yOqIgdTwx0117pWmFZSm+MPjbOfkQt9xiiX3A8MVBxAb39SmsQzePWzIhBnUVzQ2+cB+HbyBkTxEngHuCWfN7oXEzi8svvkZe5Emfioyu/n0Jnfb6TielU04ja58Tc8e4AXpPvWYtoUcxoHZA1rdu0DPcdK9u8VROeR5z8Gr+ZUYb/a4ia/RJ6+zk3zjD6YI1lrUO0Xl6d+9I5RO1yGXEV4SPAuU2v80qWbS9iZseaxBVe/0FcZt7qf59LfXPK9wd+ko83J6ad7V1ivav7Qf5sXeW5NJ+vRlTullPpLmt8eUpujJVsoJ4Mhv8hm2/5+p7EQM6OdXwAba9NJfq9jqG3tvKePGg6mvu5kmXYnUr/Vx4I78nHI4gm+aeoZ9L/AcRI7qeBLwG/IM72GxKDTZfS4IyDPNDPIfpZd6y8fkQuV2NTzVbyWc/NEHx+jjhRG76DOKl3Prczwv40ohn7S6JlMYdo8re6XZ6fsdPkv/b1IWrcE4mpZbfna0uJ6WC1fxbEAOxTRJdPx4OaNX02rRA+lKgJ71H5/fXkNMSuLE/pDdK+kxC1hmOIK3DOJ2oorQNlFtF533GNlKjxXgmcR1yJ9eoM4dOIeahfaOoAIfpYH6P3Sr0DiBHx7SrvuY3Orzjbl7iYobqDnUPcz2Arouvh7AyI5vq5ov/zLGI2ycW5zX/QZPC3lT+LGO1v1faPz+1bnflQ6+wD4irCXWi7xSLRxJ1RR9D3Yxmqx9UUYKvK8/fS2wU1N4+3jvq9V7Ec07sZav3ZLpUQPoqYevmeDOSH6OKFMMU3RtuG2YLeG7/0EE22S4ha1B7E9fOXMsB5kpWN3fo5l+jnPJzoT/5eHixbE/eRuJ4Grr8n5sLukY8PIQYq9iUmwZ9HdD+8iRiFv7+TEwBR03mO3lH30ZXfnUv0/Y0hTj7vpoMLOvq5PGMy8M7JANyiwbLWqDyeT/Rrnk3Uco/P1+cQl77u0sX9ezbR3dVI0K2i3AV5XN1KTAFbl97+z0uJluXELixHiQG3PsvMfGnlwew8Vj5Gjd1v/Vq+bm+Qto0wgRgQ6iH6iH4O/GPl9y/LHeYq4gbo+1CpzQ2gnEltf3M+sH/ltYOJ2Q+t7odG7u+QB8Ld9F59NJsY/d+dGHU+gah530DW1jos74A8uayXz6s1sTvpnbo3ZG+CPch1/iei1r0zsCxff1ee1D5aCeFjunHAEU3++UQzvNuX2M6gd0D5PPL+FhnCRxJdIo0OMBfcF6otgP2I1sgUYEzr95UQ3o8GW4ErXcbCG2hO2wY5j2gCbFR5zxiiv641kXuF2mw/yjiQmP6yOjGl6wPElVc3Vd7zCqLW29F9Dvq5I5xM9MXuns8PyxBuXRM/hhr6ftt2vIfJGRT0Nrlvpst32erC/tSa+nVwZVtukKF8J3ExyznElLvju7hcY3IZulrzzbJ3IKaWnUf0Sbc+/67V/Ausc3u/9wKi338x0erZq/re/mZJI8s6BDbW+sSo9Bvz+YW5kfrsZhjIxqL3xh5T8kC8rRLgdxJNjhHEgNDXaP7GOq2v2DmhLYQPJUaiGxkh7iOEj8lt3Oj6dnk/ap/6NSZPuhsStd8z8vXjiFrwsFn3yjZoDx4jupi+SdzEqbXvzyFaYuuUDJ8Gt8O4/NlqWX8in88numF6iFkPxde969/CWvkKFs+fvzGzXxJf+PcXd19oZhcAXzKzvT2/HaGl9f/6Uc7exIDH3cRA3onE9LWtiFA+kJgZcB3xIb3d3X9TxzquZHm2A043s+XufnluhzPN7H3ufqOZ/YXoE66du38hv+Hhq2b2YWKua6PrW8DTxGDKn8xsNHEF2lRiLuq6xI3ENye6ew4cZusOrHAT8VOI4P05MYZyCXHSP8nMXkF0uR3p7v9daFEbkcfUeOBnZnaku3/GzH4HPGZm1xMnnAM9vm7qMOKE/WjBRe5uAJvZ6u7+dD5+A7Gx7nH3s/LO+8fllzKcYWarEf2iv1r5X1xpOdOJe0ecStSMdiCappsAO5vZE+7+S2BGfr3PCHd/ooZVbJW/wkkmH3/XzL4N7GNmz7n7R8zMgYvNbL67f6au8vuSITyCmN72Wnf/9ybLK+D3RBP774n51LcTF5U8RMxHvYaYDnWBu3flmzW6Jb8B5ql8PJWY9XEFEcLXEC2e3xDTD0cQ0zt/VGZpm5UVuuOAj5nZW939s2b2JHGRzTvc/RkzO5ZoFd1VdGHp4nfCWXx9+k3kpcPEtKufEBPBb8mz1QJiUO4j7v7VDsraiejr+np+z9gRxPeYrU1c/nk3cKe7/6KTdVpF+SPd/Zl8vA/R3F2az99J3Avhk+5+a+4st7v7fzSxLH0s2/MH63BjZi8jphO+Cri5crK/FviMu99YcvmaYGYHEANtFxG1+5OAizy+u2w8cXvFbYH53drHhgIz25cYwJ9JnITPIbohHyMGZw8bCpWQrn4pp5ktpPc2d2e7+w/M7HjioLktQ/h04FZ3/24N5fVkc2MKcT+HJ4krvjYjTgDLvObvcTOzGUQ/4wPE4B/EtLcl7n5DvmcJUTs5092/UGf5siIzm01MLTzM3R8uvTx1yu8HPJ+438LNZvYqYj7v1939hHzPekR3zCbEMfCsuz9Xapmb0DrO8/GRxPjRxWY2ixhf2t/d785W93rAA0PlZNSVLojWlz26+4Vm9jgx9/BaYjL+DYADM/PLJS+qq9zWh+LuP8w+oMOJfsKHgDsaCN99iYs4lhKDi/sSlzYuAf46t8MniXuwjibmhEoDzGwi8XnPJb45ZbiF7wTioqE57v4tM1vT3R8xs5OApWY2z90/5O6/NbPFxNTKYt8y3BQzew2w2MxmufuTRC33cQB3X25mzwE3m9kcd/90yWXtS+MB3Arf7Jv6g7tfbfE12xea2aPufp+ZLSf6phrrl8oQXg4cRNyR6rd1/n0zW5cYaZ6Z/U4bEc3C1YkQBnifmc0k7knw5uE4EDSE/J642GTmcOvzTe2Dju82sz2JQaVHgIVmNt7dz3b33xVczka5+wNm9gywzMzeTAy0PV75/adyTOYSM/sS8NRQagF0pQvCzPYj7vh/rLvfla+dRDTVT3b3f6v2mza8LKs1VRPI/riLiDmWT5jZPwNfdfcr8vfbEHfEun2YhoJ0SYbKAuJm9q1Bx7uJ1t2biBA6mDjRP1ZqOZuS69/TasWa2Y3E/Swezp8PEScpiCmmT7n7H0ss66o0HsBmtgFRM5zr7t/MJsNYonZyCDFo8Abgf4fSmWmw8mRzCTEi/0rgKHf/Y6slUHbpZDhZxaDjdUQ32O3DcZ+rHktmtkFrqqqZXUF0OV1BzHgZS8wHP2Oo9Pm2qz2AzWxr4tLGZfl8LeK+o08R0842J667vsHdrzKzTdz9Z7UuRGFmthdx0ceEnBYz2t3/VHq5ZPirDDoePhxbWW3hO4+4mc59xPfMfd/MLiMueDoo3zPK3f9cbolXrafOP2ZmWxBfZbJm6zV3/wNx4cMo4vLfGcRc1B3z98MqfAHc/Xbi0tM7zGx9ha80zcwmmtl8YrrVscMxfGGFi00OJu41PY+44u94M9vF3U8Gesys1ffbeLdmJ2obhMupXrcAy919Sb42JvtdlhLfE/Wsme1MXJW2qK6yh6K88GEUcKuZvS5eGn7NQRkyhvug4/PMbEtittH1OYj/U+JLHI7ImVQHmtkr83gb0sdcLTXg7Hb4OHHp4x/MbFeA7PvclLjv7gSLy3HnE/MWb80z1LDl7jcT93t4TuErTXL3P7r754Zj+FpcPl31BNGKPiprvf9N3Gf6z8BB2eX3624v52B03AdsZmOIQbariBrwaWR3A3HP3ZuJieHn5/snuPt/aVBKRF5I1na/T3yN/UPu/tF8fTRxVe104vLye3JQcrS7P77SPzjE1DII1wrVfDyF6BgfSQTwj9z9werVKiIi/WFmGxL39PgsEbaPEpcY/6u7P2lmJxMX3Jzu7t8ot6SDU0sXRCV8e9z9h0Sf7zPEBQdr53sUviIyIB43zfomcUOt/YlLrecCn8+xlQeIG28N+KZdQ0GtsyAql/7+mAjh0USfzDp1liMiw19ljGgRMZg2Dvgv4uZCPyC+x+0I4ls+HimykB1q9EIMM5sMzweyiMiAZAivRlxLsCkxfXWRu9+U014f8xfxfY27ejc0EZHByLGlrwCXufv7Sy9PXWrtghARaUKOLS0CRpjZGqWXpy4KYBF5sfgGMRg3bKgLQkReNGyYfaOLAlhEpBB1QYiIFKIAFhEpRAEsIlKIAlhEpBAFsIhIIQpgEZFC/g8uWIWo14sBuAAAAABJRU5ErkJggg==",
            "text/plain": [
              "<Figure size 432x288 with 1 Axes>"
            ]
          },
          "metadata": {
            "needs_background": "light"
          },
          "output_type": "display_data"
        }
      ],
      "source": [
        "plot_value_array(0, predictions_single, test_labels)\n",
        "_ = plt.xticks(range(10), class_names, rotation=45)"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 25,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "kxJi-t0j8c9A",
        "outputId": "33ac3cf0-933a-4f79-deba-0abf16d3e685"
      },
      "outputs": [
        {
          "data": {
            "text/plain": [
              "4"
            ]
          },
          "execution_count": 25,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "np.argmax(predictions_single[0])"
      ]
    }
  ],
  "metadata": {
    "accelerator": "GPU",
    "colab": {
      "collapsed_sections": [],
      "name": "Intro to Deep Learning for Images classification",
      "provenance": [],
      "toc_visible": true
    },
    "gpuClass": "standard",
    "kernelspec": {
      "display_name": "Python 3.8.10 64-bit",
      "language": "python",
      "name": "python3"
    },
    "language_info": {
      "name": "python",
      "version": "3.8.10"
    },
    "vscode": {
      "interpreter": {
        "hash": "916dbcbb3f70747c44a77c7bcd40155683ae19c65e1c03b4aa3499c5328201f1"
      }
    },
    "widgets": {
      "application/vnd.jupyter.widget-state+json": {
        "00af9da286054a2f9e2c33d13e2d1490": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HTMLModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HTMLModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HTMLView",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_e717fabe52c648209ba8089ceb233f55",
            "placeholder": "​",
            "style": "IPY_MODEL_ad63069f2f9f449b8cd772f0238bd3ba",
            "value": " 9999/10000 [00:00&lt;00:00, 124723.71 examples/s]"
          }
        },
        "045ebc8d71cd4b409c9982bff55a9462": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "DescriptionStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "DescriptionStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "description_width": ""
          }
        },
        "07af05b798054560a54d85730a5148be": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HTMLModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HTMLModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HTMLView",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_17256531b0914552bf0758666d601645",
            "placeholder": "​",
            "style": "IPY_MODEL_57ddcc781d764f439010508da5cc1d61",
            "value": " 4/4 [00:03&lt;00:00,  1.40 url/s]"
          }
        },
        "092db04522ff4fc59a1ddea2839ca336": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "FloatProgressModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "FloatProgressModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "ProgressView",
            "bar_style": "success",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_6296cb36821745a5bd73776a7605940c",
            "max": 1,
            "min": 0,
            "orientation": "horizontal",
            "style": "IPY_MODEL_318473cb3bdb47838493752e11184ee5",
            "value": 1
          }
        },
        "0cd6b0ba936648038e2a7c1edf8c13bf": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "DescriptionStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "DescriptionStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "description_width": ""
          }
        },
        "154d490f83384f85a9ab454ffbf5743d": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "ProgressStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "ProgressStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "bar_color": null,
            "description_width": ""
          }
        },
        "17256531b0914552bf0758666d601645": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "173b870dc7d34f649a2c94bcfcff72fc": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "FloatProgressModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "FloatProgressModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "ProgressView",
            "bar_style": "success",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_96b8adde241e4ebb91107228e459de4c",
            "max": 1,
            "min": 0,
            "orientation": "horizontal",
            "style": "IPY_MODEL_d1231e61faaa4619be6a234fd821037d",
            "value": 1
          }
        },
        "1965c84f87e14e1aabd14a4d0e859284": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "19a370bdb7c14cbba2d997fd21e6658e": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "FloatProgressModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "FloatProgressModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "ProgressView",
            "bar_style": "danger",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_9cd14d5404b049dcbe535827d6e4a224",
            "max": 10000,
            "min": 0,
            "orientation": "horizontal",
            "style": "IPY_MODEL_74dc651dec6840cbac15ff24366221d4",
            "value": 9999
          }
        },
        "1a83e61052014ade94c318ef61884cea": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "DescriptionStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "DescriptionStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "description_width": ""
          }
        },
        "1c6b5940911a4f059c830053b68aa7bf": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "20f2fba8b7424d6099d4a15522061417": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "269ae71402544d258b59f265c9352134": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "2df75c343163464390df367797b03287": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HBoxModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HBoxModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HBoxView",
            "box_style": "",
            "children": [
              "IPY_MODEL_62a4796e16b74bfe9f83ae43b720a9df",
              "IPY_MODEL_092db04522ff4fc59a1ddea2839ca336",
              "IPY_MODEL_07af05b798054560a54d85730a5148be"
            ],
            "layout": "IPY_MODEL_a6e1d2d13417402a94c13fbcfc4a38b3"
          }
        },
        "2e22f492d30d4271a5c15819b3898a9f": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "DescriptionStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "DescriptionStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "description_width": ""
          }
        },
        "2eabbd90ae944a12affe7ac1baedea6b": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HTMLModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HTMLModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HTMLView",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_6b5d3ef3a3c64f32b53fe2382c37b02b",
            "placeholder": "​",
            "style": "IPY_MODEL_3860220eeda8448fb840c232f8bbc7d7",
            "value": "Dl Size...: 100%"
          }
        },
        "2fcda1efbe9c4efe8675de75e629a21b": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "318473cb3bdb47838493752e11184ee5": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "ProgressStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "ProgressStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "bar_color": null,
            "description_width": ""
          }
        },
        "375caaa2e2cf46ee84e069715e58526d": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": "20px"
          }
        },
        "3860220eeda8448fb840c232f8bbc7d7": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "DescriptionStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "DescriptionStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "description_width": ""
          }
        },
        "3c06489d7c08415db37da297301e5691": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "FloatProgressModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "FloatProgressModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "ProgressView",
            "bar_style": "success",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_375caaa2e2cf46ee84e069715e58526d",
            "max": 1,
            "min": 0,
            "orientation": "horizontal",
            "style": "IPY_MODEL_154d490f83384f85a9ab454ffbf5743d",
            "value": 1
          }
        },
        "408db07d4d984e6c887eefa633a72a2e": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "488fa7647d024200bc6c9a78038b4fba": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "4c541d150a2849339653b969e9d33abc": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HTMLModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HTMLModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HTMLView",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_5c10d39849464fd0bbd6e22be13ce254",
            "placeholder": "​",
            "style": "IPY_MODEL_6deff8ebd6eb434d943f22e505ea3670",
            "value": ""
          }
        },
        "55209c0f729547bb843a0184db07b1cc": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "DescriptionStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "DescriptionStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "description_width": ""
          }
        },
        "5524d6c3ebad4a7ebda398d43d8488b7": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HTMLModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HTMLModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HTMLView",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_88ba38d6890c4680a5af173738fa6003",
            "placeholder": "​",
            "style": "IPY_MODEL_1a83e61052014ade94c318ef61884cea",
            "value": " 29/29 [00:03&lt;00:00, 19.22 MiB/s]"
          }
        },
        "576dbf67ce624ab8b371d6491f999769": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "FloatProgressModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "FloatProgressModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "ProgressView",
            "bar_style": "danger",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_488fa7647d024200bc6c9a78038b4fba",
            "max": 60000,
            "min": 0,
            "orientation": "horizontal",
            "style": "IPY_MODEL_75c7636a4b014a2f868942e4134dcbac",
            "value": 59999
          }
        },
        "57ddcc781d764f439010508da5cc1d61": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "DescriptionStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "DescriptionStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "description_width": ""
          }
        },
        "5a8a389390924d6d81e0ac38cdc60ed6": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HTMLModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HTMLModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HTMLView",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_b09f8a68397743dab901b9b6cfa44642",
            "placeholder": "​",
            "style": "IPY_MODEL_66bc597581ab422cb4e302d88165e633",
            "value": "100%"
          }
        },
        "5ba3be176838422a9d4a490d47fcbcdb": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "5c10d39849464fd0bbd6e22be13ce254": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "61d78a74b4f847b580911cb7054fb4d3": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HTMLModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HTMLModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HTMLView",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_2fcda1efbe9c4efe8675de75e629a21b",
            "placeholder": "​",
            "style": "IPY_MODEL_2e22f492d30d4271a5c15819b3898a9f",
            "value": ""
          }
        },
        "6296cb36821745a5bd73776a7605940c": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": "20px"
          }
        },
        "62a4796e16b74bfe9f83ae43b720a9df": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HTMLModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HTMLModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HTMLView",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_1c6b5940911a4f059c830053b68aa7bf",
            "placeholder": "​",
            "style": "IPY_MODEL_b7de0805b33b4fffa35a68dbfc9fa07f",
            "value": "Dl Completed...: 100%"
          }
        },
        "66bc597581ab422cb4e302d88165e633": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "DescriptionStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "DescriptionStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "description_width": ""
          }
        },
        "6af42b282e27419c8940a7cd2901117b": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HTMLModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HTMLModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HTMLView",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_5ba3be176838422a9d4a490d47fcbcdb",
            "placeholder": "​",
            "style": "IPY_MODEL_0cd6b0ba936648038e2a7c1edf8c13bf",
            "value": " 4/4 [00:03&lt;00:00,  1.04 file/s]"
          }
        },
        "6b5d3ef3a3c64f32b53fe2382c37b02b": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "6c7b9d968c024e7ab94499e852a72b02": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HTMLModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HTMLModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HTMLView",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_77c7d6a33ec141e58bb2d4a93342d83d",
            "placeholder": "​",
            "style": "IPY_MODEL_045ebc8d71cd4b409c9982bff55a9462",
            "value": " 59999/60000 [00:00&lt;00:00, 224457.58 examples/s]"
          }
        },
        "6dc2952c05064b0dac0d50749e9ca163": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "6deff8ebd6eb434d943f22e505ea3670": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "DescriptionStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "DescriptionStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "description_width": ""
          }
        },
        "6ed2836d940f40c58e930da6dcf3be46": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "DescriptionStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "DescriptionStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "description_width": ""
          }
        },
        "74dc651dec6840cbac15ff24366221d4": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "ProgressStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "ProgressStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "bar_color": null,
            "description_width": ""
          }
        },
        "75c7636a4b014a2f868942e4134dcbac": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "ProgressStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "ProgressStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "bar_color": null,
            "description_width": ""
          }
        },
        "77c7d6a33ec141e58bb2d4a93342d83d": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "7d1d2609565d4c7388763c542ca5a2aa": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HTMLModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HTMLModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HTMLView",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_20f2fba8b7424d6099d4a15522061417",
            "placeholder": "​",
            "style": "IPY_MODEL_6ed2836d940f40c58e930da6dcf3be46",
            "value": " 59954/0 [00:47&lt;00:00, 1456.63 examples/s]"
          }
        },
        "8270ae33d035459ca42f9c59b8eaa3da": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "88ba38d6890c4680a5af173738fa6003": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "8ada5f761f214be887f207073ef28b5b": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "93f0bba3a59f452c844c4e06314ebb9e": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "94143fc52b7949e99511fdd34e0406dc": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "96b8adde241e4ebb91107228e459de4c": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": "20px"
          }
        },
        "972c505f816d4414913fbb73cd2436fb": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HBoxModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HBoxModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HBoxView",
            "box_style": "",
            "children": [
              "IPY_MODEL_c46402005c874fae9c36bdef235a091a",
              "IPY_MODEL_19a370bdb7c14cbba2d997fd21e6658e",
              "IPY_MODEL_00af9da286054a2f9e2c33d13e2d1490"
            ],
            "layout": "IPY_MODEL_93f0bba3a59f452c844c4e06314ebb9e"
          }
        },
        "975cf3e668ea4ad99f3cf1fe35c44c81": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HBoxModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HBoxModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HBoxView",
            "box_style": "",
            "children": [
              "IPY_MODEL_e969e53722dc4da996f2a057ab29422e",
              "IPY_MODEL_3c06489d7c08415db37da297301e5691",
              "IPY_MODEL_6af42b282e27419c8940a7cd2901117b"
            ],
            "layout": "IPY_MODEL_269ae71402544d258b59f265c9352134"
          }
        },
        "98365ff527ba429aafc5398b72382054": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "9c71a40348394f9993b9a6afdb6d8ed7": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HBoxModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HBoxModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HBoxView",
            "box_style": "",
            "children": [
              "IPY_MODEL_61d78a74b4f847b580911cb7054fb4d3",
              "IPY_MODEL_fa030d8a56de418b9c27c00259898a10",
              "IPY_MODEL_7d1d2609565d4c7388763c542ca5a2aa"
            ],
            "layout": "IPY_MODEL_8ada5f761f214be887f207073ef28b5b"
          }
        },
        "9cd14d5404b049dcbe535827d6e4a224": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "a00d66d782a84ec48be6baee1647340f": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "ProgressStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "ProgressStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "bar_color": null,
            "description_width": ""
          }
        },
        "a6e1d2d13417402a94c13fbcfc4a38b3": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "ad63069f2f9f449b8cd772f0238bd3ba": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "DescriptionStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "DescriptionStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "description_width": ""
          }
        },
        "b09f8a68397743dab901b9b6cfa44642": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "b7de0805b33b4fffa35a68dbfc9fa07f": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "DescriptionStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "DescriptionStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "description_width": ""
          }
        },
        "bc2348dcbde2414bb99729662a3763f5": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HBoxModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HBoxModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HBoxView",
            "box_style": "",
            "children": [
              "IPY_MODEL_4c541d150a2849339653b969e9d33abc",
              "IPY_MODEL_c77fdab52ff24f41b2c2ea7f9619f1f7",
              "IPY_MODEL_c77ac8dc74aa4b919227e8d94e97a48e"
            ],
            "layout": "IPY_MODEL_94143fc52b7949e99511fdd34e0406dc"
          }
        },
        "bdb7dc2a1019442a94d80a2dd85f0a01": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": "20px"
          }
        },
        "c46402005c874fae9c36bdef235a091a": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HTMLModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HTMLModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HTMLView",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_8270ae33d035459ca42f9c59b8eaa3da",
            "placeholder": "​",
            "style": "IPY_MODEL_e0db0a4020b6440486ecce82ffac32a3",
            "value": "100%"
          }
        },
        "c77ac8dc74aa4b919227e8d94e97a48e": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HTMLModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HTMLModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HTMLView",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_98365ff527ba429aafc5398b72382054",
            "placeholder": "​",
            "style": "IPY_MODEL_d16c627c81064dd3b9a2d3291e703388",
            "value": " 9877/0 [00:06&lt;00:00, 1455.99 examples/s]"
          }
        },
        "c77fdab52ff24f41b2c2ea7f9619f1f7": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "FloatProgressModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "FloatProgressModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "ProgressView",
            "bar_style": "info",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_bdb7dc2a1019442a94d80a2dd85f0a01",
            "max": 1,
            "min": 0,
            "orientation": "horizontal",
            "style": "IPY_MODEL_f4e51270bf8f47f18591b5ede0cf22ce",
            "value": 1
          }
        },
        "cb78a473b6c34646bf30a201c7f5598e": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HBoxModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HBoxModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HBoxView",
            "box_style": "",
            "children": [
              "IPY_MODEL_2eabbd90ae944a12affe7ac1baedea6b",
              "IPY_MODEL_173b870dc7d34f649a2c94bcfcff72fc",
              "IPY_MODEL_5524d6c3ebad4a7ebda398d43d8488b7"
            ],
            "layout": "IPY_MODEL_408db07d4d984e6c887eefa633a72a2e"
          }
        },
        "cc27b05b821445c7aa7e522c8e169b61": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": "20px"
          }
        },
        "d1231e61faaa4619be6a234fd821037d": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "ProgressStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "ProgressStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "bar_color": null,
            "description_width": ""
          }
        },
        "d16c627c81064dd3b9a2d3291e703388": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "DescriptionStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "DescriptionStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "description_width": ""
          }
        },
        "e0db0a4020b6440486ecce82ffac32a3": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "DescriptionStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "DescriptionStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "description_width": ""
          }
        },
        "e717fabe52c648209ba8089ceb233f55": {
          "model_module": "@jupyter-widgets/base",
          "model_module_version": "1.2.0",
          "model_name": "LayoutModel",
          "state": {
            "_model_module": "@jupyter-widgets/base",
            "_model_module_version": "1.2.0",
            "_model_name": "LayoutModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "LayoutView",
            "align_content": null,
            "align_items": null,
            "align_self": null,
            "border": null,
            "bottom": null,
            "display": null,
            "flex": null,
            "flex_flow": null,
            "grid_area": null,
            "grid_auto_columns": null,
            "grid_auto_flow": null,
            "grid_auto_rows": null,
            "grid_column": null,
            "grid_gap": null,
            "grid_row": null,
            "grid_template_areas": null,
            "grid_template_columns": null,
            "grid_template_rows": null,
            "height": null,
            "justify_content": null,
            "justify_items": null,
            "left": null,
            "margin": null,
            "max_height": null,
            "max_width": null,
            "min_height": null,
            "min_width": null,
            "object_fit": null,
            "object_position": null,
            "order": null,
            "overflow": null,
            "overflow_x": null,
            "overflow_y": null,
            "padding": null,
            "right": null,
            "top": null,
            "visibility": null,
            "width": null
          }
        },
        "e9548d82467f471981626fdf90d5b84d": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HBoxModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HBoxModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HBoxView",
            "box_style": "",
            "children": [
              "IPY_MODEL_5a8a389390924d6d81e0ac38cdc60ed6",
              "IPY_MODEL_576dbf67ce624ab8b371d6491f999769",
              "IPY_MODEL_6c7b9d968c024e7ab94499e852a72b02"
            ],
            "layout": "IPY_MODEL_1965c84f87e14e1aabd14a4d0e859284"
          }
        },
        "e969e53722dc4da996f2a057ab29422e": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "HTMLModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "HTMLModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "HTMLView",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_6dc2952c05064b0dac0d50749e9ca163",
            "placeholder": "​",
            "style": "IPY_MODEL_55209c0f729547bb843a0184db07b1cc",
            "value": "Extraction completed...: 100%"
          }
        },
        "f4e51270bf8f47f18591b5ede0cf22ce": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "ProgressStyleModel",
          "state": {
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "ProgressStyleModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/base",
            "_view_module_version": "1.2.0",
            "_view_name": "StyleView",
            "bar_color": null,
            "description_width": ""
          }
        },
        "fa030d8a56de418b9c27c00259898a10": {
          "model_module": "@jupyter-widgets/controls",
          "model_module_version": "1.5.0",
          "model_name": "FloatProgressModel",
          "state": {
            "_dom_classes": [],
            "_model_module": "@jupyter-widgets/controls",
            "_model_module_version": "1.5.0",
            "_model_name": "FloatProgressModel",
            "_view_count": null,
            "_view_module": "@jupyter-widgets/controls",
            "_view_module_version": "1.5.0",
            "_view_name": "ProgressView",
            "bar_style": "info",
            "description": "",
            "description_tooltip": null,
            "layout": "IPY_MODEL_cc27b05b821445c7aa7e522c8e169b61",
            "max": 1,
            "min": 0,
            "orientation": "horizontal",
            "style": "IPY_MODEL_a00d66d782a84ec48be6baee1647340f",
            "value": 1
          }
        }
      }
    }
  },
  "nbformat": 4,
  "nbformat_minor": 0
}
