---
title: "Instalación de Python en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 7/13/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce3d3656-7ba2-490d-92df-0bb3e3badf92
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 613af31a2e44cc447980b68de4b0b5642dde1262
ms.contentlocale: es-es
ms.lasthandoff: 07/18/2017

---

# <a name="installing-python-support-in-visual-studio-on-windows"></a>Instalación de la compatibilidad con Python en Visual Studio en Windows

Para instalar la compatibilidad de Python para Visual Studio, siga las instrucciones que aparecen en la sección correspondiente a su versión de Visual Studio:

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 y anterior](#visual-studio-2013-and-earlier)

Para Visual Studio 2015 y versiones anteriores también es necesario instalar por separado un intérprete de Python de su elección. Para obtener más información, consulte [Entornos de Python](python-environments.md).

Para probar rápidamente la compatibilidad de Python después de seguir los pasos de instalación, abra la ventana interactiva de Python; para ello, presione Alt-I y escriba `2+2`. Si no ve la salida de `4`, revise los pasos.

> [!Tip]
> La carga de trabajo de Python incluye la útil extensión Cookiecutter que proporciona una interfaz gráfica de usuario para detectar plantillas, opciones de plantilla de entrada y crear proyectos y archivos. Para obtener más información, consulte [Uso de la extensión Cookiecutter](cookiecutter.md).

> [!Note]
> La compatibilidad con Python no está actualmente disponible en Visual Studio para Mac, pero está disponible en Mac y Linux a través de Visual Studio Code. Consulte las [Preguntas y respuestas](python-in-visual-studio.md#questions-and-answers).

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. Instale Visual Studio 2017 desde [https://www.visualstudio.com/vs/](https://www.visualstudio.com/vs/).

1. En el instalador de Visual Studio, seleccione la carga de trabajo **Web y nube > Desarrollo de Python**.

    ![Carga de trabajo de desarrollo de Python en el instalador de Visual Studio](media/installation-python-workload.png)

    > [!Note]
    > Python también se incluye en la carga de trabajo **Aplicaciones de ciencia de datos y de análisis**.

1. En el lado derecho del instalador, seleccione los intérpretes de Python y otras herramientas relacionadas que desee incluir. Por ejemplo, si va a desarrollar extensiones de C++ para Python, incluya la opción **Herramientas de desarrollo nativo Python**.

    ![Opciones de desarrollo de Python en el instalador de Visual Studio](media/installation-python-options.png)

1. Si ya tiene instalados intérpretes en el equipo, consulte [Creación de un entorno para un intérprete existente](python-environments.md#creating-an-environment-for-an-existing-interpreter).

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Ejecute el instalador de Visual Studio; para ello, vaya a **Panel de control > Programas y características**, seleccione **Microsoft Visual Studio 2015** y después haga clic en **Cambiar**.

1. En el instalador, seleccione **Modificar**.

1. Seleccione **Lenguajes de programación > Herramientas de Python para Visual Studio** y luego haga clic en **Siguiente**:

    ![Opción de PTVS en el instalador de Visual Studio 2015](media/installation-vs2015.png)    

1. Una vez completada la instalación de Visual Studio, [instale un intérprete de Python de su elección](python-environments.md#selecting-and-installing-python-interpreters). Si ya tiene instalado un intérprete, consulte [Creación de un entorno para un intérprete existente](python-environments.md#creating-an-environment-for-an-existing-interpreter).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 y anterior

1. Instale la versión adecuada de Herramientas de Python para Visual Studio para su versión de Visual Studio:

    - Visual Studio 2013: [PTVS 2.2 para Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2). En el cuadro de diálogo **Archivo > Nuevo proyecto** de Visual Studio 2013 se ofrece un acceso directo a este proceso.
    - Visual Studio 2012: [PTVS 2.1 para Visual Studio 2012](https://pytools.codeplex.com/downloads/get/920478)
    - Visual Studio 2010: [PTVS 2.1 para Visual Studio 2010](https://pytools.codeplex.com/downloads/get/920479)

1. [Instale un intérprete de Python de su elección](python-environments.md#selecting-and-installing-python-interpreters). Si ya tiene instalado un intérprete, consulte [Creación de un entorno para un intérprete existente](python-environments.md#creating-an-environment-for-an-existing-interpreter).

## <a name="install-locations"></a>Ubicaciones de instalación

De forma predeterminada, la compatibilidad de Python se instala para todos los usuarios de un equipo.

En Visual Studio 2017, la carga de trabajo de Python se instala en `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\<VS_edition>Common7\IDE\Extensions\Microsoft\Python`, donde &lt;VS_edition&gt; es Community, Professional o Enterprise.

En Visual Studio 2015 y versiones anteriores, las rutas de instalación son las siguientes:

- 32 bits:
  - Ruta de acceso: `%Program Files(x86)%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Ubicación del Registro de ruta de acceso: `HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\<VS_ver>\InstallDir`
- 64 bits:
  - Ruta de acceso: `%Program Files%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Ubicación del Registro de ruta de acceso: `HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\<VS_ver>\InstallDir`

donde:

- &lt;VS_ver&gt; es:    
    - 14.0 para Visual Studio 2015
    - 12.0 para Visual Studio 2013
    - 11.0 para Visual Studio 2012
    - 10.0 para Visual Studio 2010
- &lt;PTVS_ver&gt; es un número de versión, como 2.2, 2.1, 2.0, 1.5, 1.1 o 1.0.

### <a name="user-specific-installations-15-and-earlier"></a>Instalaciones específicas de usuario (1.5 y anteriores)

Herramientas de Python para Visual Studio 1.5 y las versiones anteriores permitían una instalación solo para el usuario actual, en cuyo caso la ruta de instalación es `%LocalAppData%\Microsoft\VisualStudio\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`, donde &lt;VS_ver&gt; y &lt;PTVS_ver&gt; se corresponden con las mismas versiones indicadas anteriormente.

