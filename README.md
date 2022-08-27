# Old-TLS-detector

{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "name": " Old-TLS-detector.ipynb",
      "provenance": []
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    },
    "language_info": {
      "name": "python"
    }
  },
  "cells": [
    {
      "cell_type": "code",
      "execution_count": 1,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "BUCKUwIQ5ehJ",
        "outputId": "ceb8ba23-f9c3-4565-f422-fe71bcebb8f9"
      },
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Reading package lists... Done\n",
            "Building dependency tree       \n",
            "Reading state information... Done\n",
            "The following package was automatically installed and is no longer required:\n",
            "  libnvidia-common-460\n",
            "Use 'apt autoremove' to remove it.\n",
            "The following additional packages will be installed:\n",
            "  liblinear3 liblua5.3-0 libpcap0.8\n",
            "Suggested packages:\n",
            "  liblinear-tools liblinear-dev ndiff\n",
            "The following NEW packages will be installed:\n",
            "  liblinear3 liblua5.3-0 libpcap0.8 nmap\n",
            "0 upgraded, 4 newly installed, 0 to remove and 20 not upgraded.\n",
            "Need to get 5,446 kB of archives.\n",
            "After this operation, 24.9 MB of additional disk space will be used.\n",
            "Get:1 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libpcap0.8 amd64 1.8.1-6ubuntu1.18.04.2 [118 kB]\n",
            "Get:2 http://archive.ubuntu.com/ubuntu bionic/main amd64 liblinear3 amd64 2.1.0+dfsg-2 [39.3 kB]\n",
            "Get:3 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 liblua5.3-0 amd64 5.3.3-1ubuntu0.18.04.1 [115 kB]\n",
            "Get:4 http://archive.ubuntu.com/ubuntu bionic/main amd64 nmap amd64 7.60-1ubuntu5 [5,174 kB]\n",
            "Fetched 5,446 kB in 1s (4,698 kB/s)\n",
            "Selecting previously unselected package libpcap0.8:amd64.\n",
            "(Reading database ... 155676 files and directories currently installed.)\n",
            "Preparing to unpack .../libpcap0.8_1.8.1-6ubuntu1.18.04.2_amd64.deb ...\n",
            "Unpacking libpcap0.8:amd64 (1.8.1-6ubuntu1.18.04.2) ...\n",
            "Selecting previously unselected package liblinear3:amd64.\n",
            "Preparing to unpack .../liblinear3_2.1.0+dfsg-2_amd64.deb ...\n",
            "Unpacking liblinear3:amd64 (2.1.0+dfsg-2) ...\n",
            "Selecting previously unselected package liblua5.3-0:amd64.\n",
            "Preparing to unpack .../liblua5.3-0_5.3.3-1ubuntu0.18.04.1_amd64.deb ...\n",
            "Unpacking liblua5.3-0:amd64 (5.3.3-1ubuntu0.18.04.1) ...\n",
            "Selecting previously unselected package nmap.\n",
            "Preparing to unpack .../nmap_7.60-1ubuntu5_amd64.deb ...\n",
            "Unpacking nmap (7.60-1ubuntu5) ...\n",
            "Setting up liblinear3:amd64 (2.1.0+dfsg-2) ...\n",
            "Setting up liblua5.3-0:amd64 (5.3.3-1ubuntu0.18.04.1) ...\n",
            "Setting up libpcap0.8:amd64 (1.8.1-6ubuntu1.18.04.2) ...\n",
            "Setting up nmap (7.60-1ubuntu5) ...\n",
            "Processing triggers for man-db (2.8.3-2ubuntu0.1) ...\n",
            "Processing triggers for libc-bin (2.27-3ubuntu1.5) ...\n"
          ]
        }
      ],
      "source": [
        "!apt-get install nmap"
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "!nmap google.com -p 443 --script ssl-enum-ciphers"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "RKuOL1-Q53Ki",
        "outputId": "659be43d-731a-49cd-858d-3b983dfb3550"
      },
      "execution_count": 2,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "\n",
            "Starting Nmap 7.60 ( https://nmap.org ) at 2022-08-27 17:26 UTC\n",
            "Nmap scan report for google.com (108.177.11.113)\n",
            "Host is up (0.0012s latency).\n",
            "Other addresses for google.com (not scanned): 108.177.11.138 108.177.11.102 108.177.11.139 108.177.11.100 108.177.11.101 2607:f8b0:400c:c01::64 2607:f8b0:400c:c01::8b 2607:f8b0:400c:c01::65 2607:f8b0:400c:c01::66\n",
            "rDNS record for 108.177.11.113: vz-in-f113.1e100.net\n",
            "\n",
            "PORT    STATE SERVICE\n",
            "443/tcp open  https\n",
            "| ssl-enum-ciphers: \n",
            "|   TLSv1.0: \n",
            "|     ciphers: \n",
            "|       TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA (prime256v1) - A\n",
            "|       TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA (prime256v1) - A\n",
            "|       TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA (rsa 2048) - A\n",
            "|       TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA (rsa 2048) - A\n",
            "|       TLS_RSA_WITH_AES_128_CBC_SHA (rsa 2048) - A\n",
            "|       TLS_RSA_WITH_AES_256_CBC_SHA (rsa 2048) - A\n",
            "|       TLS_RSA_WITH_3DES_EDE_CBC_SHA (rsa 2048) - C\n",
            "|     compressors: \n",
            "|       NULL\n",
            "|     cipher preference: server\n",
            "|     warnings: \n",
            "|       64-bit block cipher 3DES vulnerable to SWEET32 attack\n",
            "|   TLSv1.1: \n",
            "|     ciphers: \n",
            "|       TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA (prime256v1) - A\n",
            "|       TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA (prime256v1) - A\n",
            "|       TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA (rsa 2048) - A\n",
            "|       TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA (rsa 2048) - A\n",
            "|       TLS_RSA_WITH_AES_128_CBC_SHA (rsa 2048) - A\n",
            "|       TLS_RSA_WITH_AES_256_CBC_SHA (rsa 2048) - A\n",
            "|       TLS_RSA_WITH_3DES_EDE_CBC_SHA (rsa 2048) - C\n",
            "|     compressors: \n",
            "|       NULL\n",
            "|     cipher preference: server\n",
            "|     warnings: \n",
            "|       64-bit block cipher 3DES vulnerable to SWEET32 attack\n",
            "|   TLSv1.2: \n",
            "|     ciphers: \n",
            "|       TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256 (prime256v1) - A\n",
            "|       TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256 (prime256v1) - A\n",
            "|       TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384 (prime256v1) - A\n",
            "|       TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA (prime256v1) - A\n",
            "|       TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA (prime256v1) - A\n",
            "|       TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256 (rsa 2048) - A\n",
            "|       TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256 (rsa 2048) - A\n",
            "|       TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384 (rsa 2048) - A\n",
            "|       TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA (rsa 2048) - A\n",
            "|       TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA (rsa 2048) - A\n",
            "|       TLS_RSA_WITH_AES_128_GCM_SHA256 (rsa 2048) - A\n",
            "|       TLS_RSA_WITH_AES_256_GCM_SHA384 (rsa 2048) - A\n",
            "|       TLS_RSA_WITH_AES_128_CBC_SHA (rsa 2048) - A\n",
            "|       TLS_RSA_WITH_AES_256_CBC_SHA (rsa 2048) - A\n",
            "|       TLS_RSA_WITH_3DES_EDE_CBC_SHA (rsa 2048) - C\n",
            "|     compressors: \n",
            "|       NULL\n",
            "|     cipher preference: server\n",
            "|     warnings: \n",
            "|       64-bit block cipher 3DES vulnerable to SWEET32 attack\n",
            "|_  least strength: C\n",
            "\n",
            "Nmap done: 1 IP address (1 host up) scanned in 1.02 seconds\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "csv = \"\"\"\n",
        "google.com\n",
        "test.com\n",
        "example.com\n",
        "\"\"\""
      ],
      "metadata": {
        "id": "JQnpm9Sd-H4j"
      },
      "execution_count": 3,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "import subprocess\n",
        "\n",
        "database = []\n",
        "\n",
        "for subdominio in csv.split(\"\\n\"):\n",
        "\n",
        "  hostinfo = \"\"\n",
        "\n",
        "  nmap = subprocess.getoutput(\"nmap \" + subdominio + \" -p 443 --script ssl-enum-ciphers\")\n",
        "\n",
        "  for linha in nmap.split(\"\\n\"):\n",
        "\n",
        "    if \"TLSv\" in linha and hostinfo == \"\":\n",
        "      hostinfo = subdominio + \",\" + linha\n",
        "\n",
        "    elif \"TLSv\" in linha and hostinfo != \"\":\n",
        "      hostinfo = hostinfo + \",\" + linha\n",
        "\n",
        "\n",
        "  if hostinfo != \"\":\n",
        "    print(hostinfo.replace(\"|   \", \"\").replace(\":\", \"\").replace(\",\", \", \"))\n",
        "\n",
        "  \n",
        "  #database.append(hostinfo)\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "X_obys_97k_I",
        "outputId": "d1b9cbb0-5987-4ade-cbf4-8f4be8fd752e"
      },
      "execution_count": 4,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "google.com, TLSv1.0 , TLSv1.1 , TLSv1.2 \n",
            "example.com, TLSv1.0 , TLSv1.1 , TLSv1.2 \n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "logs = \"\"\"google.com, TLSv1.0 , TLSv1.1 , TLSv1.2 \n",
        "teste.com, TLSv1.2 \n",
        "example.com, TLSv1.2\"\"\""
      ],
      "metadata": {
        "id": "8GYVq3RoXP4l"
      },
      "execution_count": 5,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "for linha in logs.split(\"\\n\"):\n",
        "\n",
        "  if \"TLSv1.0\" in linha or \"TLSv1.1\" in linha:\n",
        "    print(linha.replace(\",\", \":\", 1).replace(\" , \", \", \").replace(\"TLSv1.2\", \"\"))  "
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "bJzoq5AxXcZV",
        "outputId": "aba0eb90-24bb-404e-82c6-5b51b841e228"
      },
      "execution_count": 6,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "google.com: TLSv1.0, TLSv1.1,  \n"
          ]
        }
      ]
    }
  ]
}
