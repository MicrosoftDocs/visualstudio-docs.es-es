---
title: Empleo de Visual Studio for Mac Tools for Unity
description: Esta guía describe cómo usar la extensión de Visual Studio for Mac Tools for Unity
author: dantogno
ms.author: v-davian
ms.date: 07/17/2017
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: b53de918f51abd03d28173bf00d83d98503e86bd
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348935"
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>Empleo de Visual Studio for Mac Tools for Unity

En esta sección aprenderá a usar las características de productividad e integración de Visual Studio for Mac Tools for Unity y el depurador de Visual Studio para Mac para el desarrollo de Unity.

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>Apertura de scripts de Unity en Visual Studio para Mac

Una vez que Visual Studio para Mac se ha [establecido como editor de scripts externo para Unity](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac), al abrir cualquier script desde el editor de Unity se inicia o se va automáticamente a Visual Studio para Mac, con el script abierto.

También se puede abrir Visual Studio para Mac sin ningún script abierto en el editor de código fuente si se selecciona **Abrir proyecto de C#** desde el menú **Activos** de Unity.

![Abrir proyecto de C#](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Acceso a la documentación de Unity

Visual Studio for Mac Tools for Unity incluye un acceso directo para acceder a la documentación de la API de Unity. Para acceder a la documentación de la API de Unity desde Visual Studio para Mac, coloque el cursor sobre la API de Unity sobre la que quiere aprender y presione **comando ⌘ + ‘**.

## <a name="intellisense-for-unity-messages"></a>IntelliSense para mensajes de Unity
El motor de Unity difunde mensajes a scripts de MonoBehaviour, lo que permite a los desarrolladores escribir código que responda a mensajes como OnMouseDown, OnTriggerEnter, etc. Dado que estos no son métodos virtuales de la clase base de MonoBehaviour, algunos IDE como MonoDevelop carecen de la funcionalidad de completado de código para mensajes de Unity.

Pero Visual Studio for Mac Tools for Unity extiende su funcionalidad de IntelliSense a los mensajes de Unity. Esto facilita la implementación de mensajes de Unity en scripts de MonoBehaviour y ayuda con el aprendizaje de la API de Unity. Para usar IntelliSense para mensajes de Unity:

1. Coloque el cursor en una nueva línea dentro del cuerpo de una clase que derive de MonoBehaviour.

2. Comience a escribir el nombre de un mensaje de Unity, como `OnTriggerEnter`.

3. Una vez que haya escrito las letras "**ont**", aparece una lista de sugerencias de IntelliSense.

   ![Using IntelliSense](media/using-vsmac-tools-unity-image2.png)

4. La selección de la lista se puede cambiar de tres maneras:

   * Con las teclas de flecha **arriba** y **abajo**.

   * Al hacer clic con el mouse en el elemento deseado.

   * Al seguir escribiendo el nombre del elemento deseado.

5. IntelliSense puede insertar el mensaje de Unity seleccionado, incluidos todos los parámetros necesarios:

   * Al presionar **Tab**.

   * Al presionar **Entrar**.

   * Al hacer doble clic en el elemento seleccionado.

   ![Inserción de mensaje de Unity desde IntelliSense](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>Adición de nuevos archivos y carpetas de Unity

Aunque siempre puede agregar nuevos archivos a un proyecto de Unity en el editor de Unity, Visual Studio para Mac permite crear fácilmente nuevos scripts, sombreadores y carpetas de Unity desde Visual Studio.

### <a name="add-a-new-c-monobehaviour-script"></a>Adición de un nuevo script de C# de MonoBehaviour

Para agregar un nuevo script de C# de MonoBehaviour, **haga clic con el botón derecho en la carpeta Activos** o uno de sus subdirectorios en el Panel de solución y seleccione **Agregar > Nuevo MonoBehaviour**.

![Adición de nuevo MonoBehaviour](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>Adición de un nuevo sombreador de Unity

Para agregar un nuevo sombreador de Unity, **haga clic con el botón derecho en la carpeta Activos** o en un subdirectorio en el Panel de solución y seleccione **Agregar > Nuevo sombreador**.

### <a name="add-a-new-folder"></a>Adición de una nueva carpeta

Para agregar una nueva carpeta, **haga clic con el botón derecho en la carpeta Activos** o en un subdirectorio en el Panel de solución y seleccione **Agregar -> Nueva carpeta**.

Estas adiciones se reflejan en la ventana de proyecto del editor de Unity.

### <a name="to-rename-a-file-or-folder"></a>Para cambiar el nombre de un archivo o una carpeta
**Haga clic con el botón derecho** en el elemento al que quiere cambiar el nombre en el Panel de solución y seleccione **Cambiar nombre...**

> [!NOTE]
> Si tiene un nuevo proyecto de Unity sin scripts y no aparece la carpeta Activos en el Panel de solución de Visual Studio para Mac, agregue un script inicial de C# desde el editor de Unity.

## <a name="unity-debugging"></a>Depuración de Unity

Se pueden depurar proyectos de Unity con Visual Studio para Mac.

### <a name="start-debugging"></a>Iniciar depuración

Para iniciar la depuración:

1. Conecte Visual Studio a Unity al hacer clic en el botón **Reproducir** o escriba **Comando + Entrar** o **F5**.

   ![Haga clic en Reproducir en Visual Studio](media/using-vsmac-tools-unity-image5.png)

2. Vaya a Unity y haga clic en el botón **Reproducir** para ejecutar el juego en el editor.

   ![Haga clic en Reproducir en Unity](media/using-vsmac-tools-unity-image6.png)

3. Cuando se ejecuta el juego en el editor de Unity mientras se está conectado a Visual Studio, cualquier punto de interrupción detectado detiene la ejecución del juego y muestra la línea de código donde el juego alcanza el punto de interrupción en Visual Studio para Mac.

### <a name="stop-debugging"></a>Detener depuración

Para detener la depuración:

1. Haga clic en el botón **Detener** de Visual Studio para Mac o presione **Mayús + Comando + Entrar**.

   ![Haga clic en Detener en Visual Studio](media/using-vsmac-tools-unity-image7.png)

Para más información sobre la depuración en Visual Studio para Mac, vea [Empleo del depurador](debugging.md).
