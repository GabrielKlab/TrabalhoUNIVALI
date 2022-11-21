# TrabalhoUNIVALI
trabalho de Introdução a ciência da computação

{
  "nbformat": 4, #implementação de referencia de formato Jupyter para versão de notebook 4.
  "nbformat_minor": 0, #converte pra formatos menores.
  "metadata": { #módulo pra explorar informações de descriação de dados.
    "colab": { #chama o codigo para o Colab Google.
      "provenance": [], #função para armazenar cache em camadas, Ex. (SFTP)
      "collapsed_sections": [], #computa expressões dentro da sessão.
      "authorship_tag": "ABX9TyMcztjp2euym69T9Uml9+nB", #Tag do autor.
      "include_colab_link": True #inclusão de link colab definida como verdadeira.
    },
    "kernelspec": { #função para fornecer suporte ao Python 3.
      "name": "python3",
      "display_name": "Python 3"
    },
    "language_info": { #tipo da linguagem.
      "name": "python"
    }
  },
  "cells": [ #referenciador de multiplos escopos de função.
    {
      "cell_type": "markdown", #escopo 1. Metadata: com identificação pra vizualização no github do tipo texto.
      "metadata": {
        "id": "view-in-github",
        "colab_type": "text"
      },
      "source": [ #função pra buscar o link referenciado.
        "<a href=\"https://colab.research.google.com/github/VielF/ColabProjects/blob/main/Exemplo_Mofologia.ipynb\" target=\"_parent\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a>"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [ #escopo para referenciar a introdução do Colaab.
        "Universidade do Vale do Itajaí<br>\n",
        "Escola do Mar, Ciência e Tecnologia<br>\n",
        "Professor Felipe Viel\n",
        "\n",
        "# Exemplo Morfologia\n",
        "\n",
        "### Tutoriais da OpenCV\n",
        "\n",
        "- https://docs.opencv.org/master/d9/df8/tutorial_root.html\n",
        "- https://www.geeksforgeeks.org/opencv-python-tutorial/"
      ],
      "metadata": { #identificador do escopo.
        "id": "hs7F3RjrUjCH"
      }
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": { #identificar da cell CODE
        "id": "9ieiSWN_Uh5b"
      },
      "outputs": [],
      "source": [ #busca os links para importar o doc. 
        "#from https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_imgproc/py_morphological_ops/py_morphological_ops.html\n",
        "import cv2\n",
        "import numpy as np\n",
        "#caso for usar o Google Colab com a OpenCV, usar a lib abaixo\n",
        "from google.colab.patches import cv2_imshow\n"
      ]
    },
    {
      "cell_type": "code",
      "source": [ #Busca e formata a imagem.
        "img = cv2.imread('j.png',0)\n", #referencia imagem.
        "img_opening = cv2.imread('j_ruido.png',0)\n", # abre a imagem
        "img_closing = cv2.imread('j_furos.png',0)\n", #fecha a imagem apos leitura.
        "altura, largura = img.shape\n", #define altura e largura da imagem de acordo com o Notebook (Jupyter).
        "kernel = np.ones((5,5),np.uint8)\n", #declaração de uma variavel kernel com matriz 5x5.
        "print(kernel)" #imprime a variavel.
      ], 
      "metadata": { #identificador dos metadados. 
        "id": "8whvZbKhU03S"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [ 
        "erosion = cv2.erode(img,kernel,iterations = 2)\n", #adiciona erosão a imagem.
        "dilation = cv2.dilate(img,kernel,iterations = 2)" #adiciona dilatação para a imagem.
      ],
      "metadata": {
        "id": "RnKcRcjsU8VP"
      },
      "execution_count": null, #contador de execução;
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [ 
        "gradient = cv2.morphologyEx(img, cv2.MORPH_GRADIENT, kernel)\n", #adiciona filtro gradiente.
        "opening = cv2.morphologyEx(img_opening, cv2.MORPH_OPEN, kernel)\n", #Abre a imagem
        "closing = cv2.morphologyEx(img_closing, cv2.MORPH_CLOSE, kernel)" #fecha a imagem
      ],
      "metadata": {#identificador
        "id": "WvTtlQWJU-tz"
      },
      "execution_count": null, 
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [ #busca em casos de outros metodos de visualização;
        "'''\n",
        "#Caso usa com Python no próprio computador\n",
        "cv2.imshow('in', img)\n",
        "cv2.imshow('erosion_out', erosion)\n",
        "cv2.imshow('dilation_out', dilation)\n",
        "cv2.imshow('opening_out', opening)\n",
        "cv2.imshow('closing_out', closing)\n",
        "cv2.imshow('gradient_out', gradient)\n",
        "'''\n",
        "#Caso use o Google Colab\n",
        "cv2_imshow(img)\n",
        "cv2_imshow(erosion)\n",
        "cv2_imshow(dilation)\n",
        "cv2_imshow(opening)\n",
        "cv2_imshow(closing)\n",
        "cv2_imshow(gradient)"
      ],
      "metadata": {
        "id": "iMJ7o6EgVA_r"
      },
      "execution_count": null,
      "outputs": []
    }
  ]
} #fim do script;
