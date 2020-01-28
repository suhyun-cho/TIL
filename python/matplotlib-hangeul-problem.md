{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## matplotlib 에서 한글 깨짐 문제 해결방법"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### 윈도우"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {},
   "outputs": [],
   "source": [
    "import matplotlib as mpl\n",
    "import matplotlib.pyplot as plt"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 3,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "버전:  3.0.3\n",
      "설치 위치:  /Users/suhyun/anaconda3/envs/suhyun/lib/python3.7/site-packages/matplotlib/__init__.py\n",
      "설정 위치:  /Users/suhyun/.matplotlib\n",
      "캐시 위치:  /Users/suhyun/.matplotlib\n",
      "설정 파일 위치:  /Users/suhyun/anaconda3/envs/suhyun/lib/python3.7/site-packages/matplotlib/mpl-data/matplotlibrc\n"
     ]
    }
   ],
   "source": [
    "print ('버전: ', mpl.__version__)\n",
    "print ('설치 위치: ', mpl.__file__)\n",
    "print ('설정 위치: ', mpl.get_configdir())\n",
    "print ('캐시 위치: ', mpl.get_cachedir())\n",
    "print ('설정 파일 위치: ', mpl.matplotlib_fname())"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "10.0\n",
      "['AppleGothic']\n"
     ]
    }
   ],
   "source": [
    "print (plt.rcParams['font.size'] ) \n",
    "print (plt.rcParams['font.family'] )"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "plt.rcParams[\"font.family\"] = 'NanumBarunGothic'"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "rc('font', family='NanumBarunGothic')\n",
    "plt.rcParams['axes.unicode_minus'] = False"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### 맥"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "import matplotlib.pyplot as plt\n",
    "from matplotlib import rc\n",
    "rc('font', family='AppleGothic')\n",
    "plt.rcParams['axes.unicode_minus'] = False"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.7.3"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
