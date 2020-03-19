---
title: Instalación de herramientas de IA
description: Describe cómo instalar herramientas de IA para Visual Studio
keywords: ai, visual studio
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: c1160c68c79dd595e82ecf761c6e441ecc906f62
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75915807"
---
# <a name="installation"></a>Instalación

Visual Studio Tools para AI se puede instalar en sistemas operativos Windows de 64 bits.

## <a name="install-visual-studio-tools-for-ai"></a>Instalar Visual Studio Tools for AI

Esta extensión funciona con Visual Studio 2015 y 2017, Community Edition o superior.

Puede descargar las herramientas desde [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.vstoolsai-vs2017) o desde Visual Studio:

1. Seleccione **Herramientas** > **Extensiones y actualizaciones**.

   ![Menú Extensiones y actualizaciones en Visual Studio](media/installation/extensions.png)

2. En el cuadro de diálogo **Extensiones y actualizaciones**, seleccione **En línea** en el lado izquierdo.
3. En el cuadro de búsqueda que se encuentra en la esquina superior derecha, escriba "tools for ai".
4. En los resultados, seleccione **Visual Studio Tools for AI**.
5. Haga clic en **Descargar**.

## <a name="prepare-your-local-machine"></a>Preparar el equipo local

Antes de entrenar modelos de aprendizaje profundo en el equipo local, asegúrese de tener instalados los requisitos previos aplicables. Asimismo, debe confirmar que tiene la versión más reciente de los controladores y las bibliotecas de la GPU NVIDIA (si tiene una). Asegúrese también de que tiene instalado Python y las bibliotecas de Python, como NumPy y SciPy, y los marcos de aprendizaje profundo adecuados, como Microsoft Cognitive Toolkit (CNTK), TensorFlow, Caffe2, MXNet, Keras, Theano, PyTorch y Chainer, que tenga previsto usar en el proyecto.

> [!NOTE]
> La introducción al software de las siguientes subsecciones se ha extraído de sus correspondientes páginas principales.

### <a name="nvidia-gpu-driver"></a>Controlador de GPU NVIDIA

Los marcos de aprendizaje profundo usan la GPU NVIDIA para permitir que los equipos aprendan a una velocidad, precisión y escala que vayan hacia una inteligencia artificial genuina. Si el equipo tiene tarjetas GPU NVIDIA, consulte [Descargas de controladores NVIDIA](https://www.nvidia.com/Download/index.aspx) o pruebe actualizar el sistema operativo para instalar el controlador más reciente.

### <a name="cuda"></a>CUDA

[CUDA](https://developer.nvidia.com/cuda-zone) es una plataforma de computación paralela y un modelo de programación inventado por NVIDIA. Permite aumentar drásticamente el rendimiento de computación al aprovechar toda la potencia de la GPU. Actualmente, los marcos de aprendizaje profundo requieren CUDA Toolkit 8.0.

Para instalar CUDA

- Visite este [sitio](https://developer.nvidia.com/cuda-80-ga2-download-archive), descargue CUDA e instálelo.
- Instale las bibliotecas en tiempo de ejecución de CUDA y, luego, agregue la ruta de acceso binaria de CUDA a la variable de entorno %PATH% o $Path.
- En Windows, esta ruta de acceso es "C:\Archivos de programa\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin" de forma predeterminada.

![Instalación de CUDA en Windows](media/installation/install_cuda_win.png)

### <a name="cudnn"></a>cuDNN

[cuDNN](https://developer.nvidia.com/cudnn) (biblioteca de red neuronal profunda de CUDA) es una biblioteca acelerada por GPU de primitivos para redes neuronales profundas de NVIDIA. Los marcos de aprendizaje profundo más recientes requieren cuDNN v6.

Para instalar cuDNN, siga estos pasos:

- Vaya a [Desarrollador de NVIDIA](https://developer.nvidia.com/rdp/cudnn-download) para descargar e instalar el paquete más reciente.
- Asegúrese de agregar el directorio que contiene el binario de cuDNN a la variable de entorno de %PATH% o $Path.
- En Windows, puede copiar cudnn64_6.dll en "C:\Archivos de programa\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin".

> [!NOTE]
> Los marcos de aprendizaje profundo anteriores, como CNTK 2.0 y TensorFlow 1.2.1, necesitan cuDNN v5.1. No obstante, puede tener varias versiones de cuDNN instaladas a la vez.

### <a name="python"></a>Plantillas de

Python ha sido el lenguaje de programación principal para las aplicaciones de aprendizaje profundo. Se necesita la distribución de Python de **64 bits** y se recomienda [Python 3.5.4](https://www.python.org/downloads/release/python-354/) para lograr la mejor compatibilidad posible.

### <a name="to-install-python-on-windows"></a>Para instalar Python en Windows

- Le sugerimos instalar solo el iniciador de Python y agregar Python a la variable de entorno %PATH%.
- Asegúrese de instalar PIP, que es el sistema de administración de paquetes que se usa para instalar y administrar los paquetes de software escritos en Python.

La propia instalación de los marcos de aprendizaje profundo se basa en PIP.

![Instalación de Python en Windows](media/installation/install_python_win.png)

Luego, debemos comprobar que Python 3.5 se ha instalado correctamente y actualizar PIP a la versión más reciente ejecutando los siguientes comandos en un terminal:

- **Windows**

  ```cmd
  C:\Users\test>python -V
  Python 3.5.4

  C:\Users\test>pip3.5 -V
  pip 9.0.1 from c:\users\test\appdata\local\programs\python\python35\lib\site-packages (python 3.5)

  C:\Users\test>python -m pip install -U pip
  ```

- **macOS**

  ```bash
  MyMac:~ test$ python3.5 -V
  Python 3.5.4

  MyMac:~ test$ pip3.5 -V
  pip 9.0.1 from /Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages (python 3.5)

  MyMac:~ test$ python3.5 -m pip install -U pip
  ```

### <a name="python-on-visual-studio"></a>Python en Visual Studio

Python es totalmente compatible con Visual Studio a través de extensiones.
Obtenga más información sobre la instalación de [Python en Visual Studio](../python/installing-python-support-in-visual-studio.md).

### <a name="numpy-and-scipy"></a>NumPy y SciPy

- **NumPy** es un paquete de procesamiento de matrices de ámbito general pensado para manipular eficazmente matrices multidimensionales de registros arbitrarios de gran tamaño, sin que ello suponga un sacrificio de la velocidad de las matrices multidimensionales más pequeñas.

- **SciPy** es un software de código abierto de matemáticas, ciencia e ingeniería que depende de NumPy. A partir de la versión 1.0.0, SciPy cuenta con un paquete wheel oficial ya creado para Windows.

Para instalar NumPy y SciPy, ejecute el siguiente comando en un terminal:

```bash
pip3.5 install -U numpy scipy
```

> [!NOTE]
> El comando anterior actualiza las versiones antiguas o no oficiales existentes (por ejemplo, paquetes de terceros de http://www.lfd.uci.edu/~gohlke/pythonlibs/ para Windows) de NumPy y SciPy a las versiones oficiales más recientes.

### <a name="microsoft-cognitive-toolkit-cntk"></a>Microsoft Cognitive Toolkit (CNTK)

[Microsoft Cognitive Toolkit](https://cntk.ai) es un kit de herramientas de aprendizaje profundo unificado que describe las redes neuronales como una serie de pasos de cálculo por medio de un gráfico dirigido. CNTK admite los lenguajes de programación Python y BrainScript.

> [!NOTE]
> Actualmente, no admite macOS.

Para instalar el paquete de Python de CNTK, consulte [cómo instalar CNTK](/cognitive-toolkit/Setup-CNTK-on-your-machine).

### <a name="tensorflow"></a>TensorFlow

[TensorFlow](https://www.tensorflow.org/) es una biblioteca de software de código abierto para realizar cálculos numéricos por medio de gráficos de flujo de datos. Vaya [aquí](https://www.tensorflow.org/install/) para obtener información detallada sobre cómo instalarla.

> [!NOTE]
> A partir de la versión 1.2, TensorFlow ya no es compatible con GPU de macOS.

### <a name="caffe2"></a>Caffe2

[Caffe2](https://caffe2.ai/) es un marco de aprendizaje profundo ligero, modular y escalable. Basado en el marco Caffe original, Caffe2 está diseñado teniendo en mente la expresión, la velocidad y la modularidad.

Actualmente, no hay disponible ningún paquete wheel de Python para Caffe2 ya creado.

Vaya [aquí](https://caffe2.ai/docs/getting-started.html) para crearlo a partir de código fuente.

### <a name="mxnet"></a>MXNet

[MXNet Apache (en proceso de creación)](https://mxnet.incubator.apache.org/) es un marco de aprendizaje profundo diseñado para ser eficaz y flexible. Permite **combinar** la [programación simbólica e imperativa](http://mxnet.io/architecture/index.html#deep-learning-system-design-concepts) para maximizar la eficacia y la productividad.

Para instalar MXNet, ejecute el siguiente comando en un terminal:

- Con GPU

  ```bash
  pip3.5 install mxnet-cu80==0.12.0
  ```

- Sin GPU

  ```bash
  pip3.5 install mxnet==0.12.0
  ```

### <a name="keras"></a>Keras

[Keras](https://keras.io/) es una API de redes neuronales de alto nivel escrita en Python que es capaz de ejecutarse sobre CNTK, TensorFlow o Theano. Se desarrolló haciendo especial hincapié en permitir una experimentación lo más rápida posible. Poder pasar de la idea al resultado en el menor tiempo posible es fundamental para realizar una investigación adecuada.

Para instalar Keras, ejecute el comando siguiente en un terminal:

```bash
pip3.5 install Keras==2.0.9
```

### <a name="theano"></a>Theano

[Theano](http://deeplearning.net/software/theano/) es una biblioteca de Python que permite definir, optimizar y evaluar eficazmente expresiones matemáticas relativas a matrices multidimensionales.

Para instalar Theano, ejecute el comando siguiente en un terminal:

```bash
pip3.5 install Theano==0.9.0
```

### <a name="pytorch"></a>PyTorch

[PyTorch](https://pytorch.org/) es un paquete de Python que proporciona dos características de alto nivel:

- Cálculo de tensores (como NumPy) con una firme aceleración de la GPU
- Redes neuronales profundas basadas en un sistema de cálculo automático de degradado basado en cinta

Para instalar PyTorch, ejecute el siguiente comando en un terminal:

- **Windows**

  Aún no hay ningún paquete Wheel oficial. Puede descargar un paquete de terceros de [Anaconda](https://anaconda.org/pytorch/repo?type=all) o la [Universidad de California](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pytorch).

  - Descomprímalo en el directorio principal, como por ejemplo, *C:\Users\test\pytorch*.
  - Agregue *C:\Users\test\pytorch\Lib\site-packages* a la variable de entorno %PYTHONPATH%.

    ```bash
    pip3 install http://download.pytorch.org/whl/cu80/torch-0.4.0-cp36-cp36m-win_amd64.whl
    pip3 install torchvision
    ```

- **macOS**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/torch-0.2.0.post3-cp35-cp35m-macosx_10_7_x86_64.whl
  ```

  > [!NOTE]
  > Los archivos binarios de macOS no admiten CUDA. Instálelo desde el origen en caso de que CUDA sea necesario.

- **Linux**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp35-cp35m-manylinux1_x86_64.whl
  ```

  > [!NOTE]
  > Este paquete único admite tanto la CPU como la GPU.

Por último, instale torchvision en un equipo que no sea Windows:

```bash
pip3.5 install torchvision
```

### <a name="chainer"></a>Chainer

[Chainer](https://chainer.org/) es un marco de aprendizaje profundo basado en Python cuya principal característica es la flexibilidad. Brinda API de diferenciación automática basadas en el enfoque de definir mediante ejecución (conocido también como gráficos de cálculo dinámicos). También ofrece API de alto nivel orientadas a objetos para generar y entrenar redes neuronales.

Para permitir la compatibilidad con CUDA, instale [CuPy](https://github.com/cupy/cupy):

```bash
pip3.5 install cupy
```

> [!NOTE]
> En Windows, necesita la versión 2015 de [Visual Studio](https://visualstudio.microsoft.com/) o [Microsoft Visual C++ Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/) para poder compilar CuPy con CUDA 8.0.

Para instalar Chainer, ejecute el comando siguiente en un terminal:

```bash
pip3.5 install chainer==3.0.0
```
