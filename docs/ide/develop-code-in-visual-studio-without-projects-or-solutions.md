---
title: Desarrollo de código sin proyectos o soluciones
ms.date: 02/21/2018
ms.topic: conceptual
helpviewer_keywords:
- open folder [Visual Studio]
- anycode [Visual Studio]
- projects and solutions, develop code without
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7a9459868d569a7466dccf92e4b548c0500bf80
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596299"
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Desarrollo de código en Visual Studio sin proyectos o soluciones

Puede abrir código desde casi cualquier tipo de proyecto basado en directorios en Visual Studio sin necesidad de un archivo de solución o proyecto. Esto significa que, por ejemplo, puede clonar un repositorio en GitHub, abrirlo directamente en Visual Studio y comenzar a desarrollar sin tener que crear una solución o proyecto. Si es necesario, puede especificar tareas de compilación personalizadas y parámetros de inicio a través de archivos JSON simples.

Una vez que abre los archivos de código en Visual Studio, el **Explorador de soluciones** muestra todos los archivos de la carpeta. Puede hacer clic en cualquier archivo para comenzar a editarlo. En segundo plano, Visual Studio comienza a indexar los archivos para habilitar las características de refactorización, navegación e IntelliSense. A medida que edita, crea, mueve o elimina archivos, Visual Studio hace seguimiento de manera automática de los cambios y actualiza de manera continua su indice de IntelliSense. El código aparecerá con coloración de sintaxis y, en muchos casos, incluye la finalización de instrucciones de IntelliSense básicas.

## <a name="open-any-code"></a>Apertura de cualquier tipo de código

Puede abrir el código en Visual Studio de una de las maneras siguientes:

- En la barra de menús de Visual Studio, elija **Archivo** > **Abrir** > **Carpeta** y vaya a la ubicación del código.

- En el menú contextual (clic derecho) de una carpeta que contiene código, elija el comando **Abrir en Visual Studio**.

::: moniker range="vs-2017"
- Elija el vínculo **Abrir carpeta** en la **página de inicio** de Visual Studio.
::: moniker-end

::: moniker range=">=vs-2019"
- Haga clic en el vínculo **Abrir carpeta** de la ventana de inicio.
::: moniker-end

- Si es usuario de teclado, presione **Ctrl**+**Mayús**+**Alt**+**O** en Visual Studio.

- Abra el código desde un repositorio GitHub clonado.

### <a name="to-open-code-from-a-cloned-github-repo"></a>Para abrir el código desde un repositorio de GitHub clonado

En el ejemplo siguiente se muestra cómo clonar un repositorio de GitHub y, a continuación, abrir su código en Visual Studio. Para seguir este procedimiento, debe tener una cuenta de GitHub y Git para Windows instalada en el sistema. Consulte [Signing up for a new GitHub account](https://help.github.com/articles/signing-up-for-a-new-github-account/) (Registro para obtener una cuenta de GitHub) y [Git for Windows](https://git-for-windows.github.io/) (Git para Windows) para obtener más información.

1. Vaya al repositorio que quiere clonar en GitHub.

1. Elija el botón **Clone or Download** (Clonar o descargar) y, después, elija el botón **Copiar en el Portapapeles** del menú desplegable para copiar la dirección URL segura del repositorio de GitHub.

   ![Botón de clonar de GitHub](./media/VSIDE_Code_Clone.png)

1. En Visual Studio, elija la pestaña **Team Explorer** para abrir **Team Explorer**. Si no ve la pestaña, ábralo desde **Ver** > **Team Explorer**.

1. En Team Explorer, en la sección **Repositorios GIT locales**, elija el comando **Clonar** y, a continuación, pegue la dirección URL de la página de GitHub en el cuadro de texto.

   ![Clonación del proyecto](./media/VSIDE_Code_Clone2.png)

1. Elija el botón **Clonar** para clonar los archivos del proyecto en un repositorio de GIT local. Dependiendo del tamaño del repositorio, este proceso podría tardar varios minutos.

1. Una vez que el repositorio se haya clonado en el sistema, en **Team Explorer**, elija el comando **Abrir** del menú contextual (clic con el botón derecho) del repositorio recién clonado.

   ![Repositorio clonado](./media/VSIDE_Code_Clone3.png)

1. Elija el comando **Mostrar vista de carpeta** para ver los archivos en el **Explorador de soluciones**.

   ![Mostrar vista de carpeta](./media/VSIDE_Code_Clone3_show.png)

   Ahora puede examinar las carpetas y los archivos del repositorio clonado y ver y buscar en el código en el editor de código de Visual Studio, con coloración de sintaxis y otras características.

## <a name="run-and-debug-your-code"></a>Ejecución y depuración del código

Puede depurar el código en Visual Studio sin un proyecto ni solución. Para depurar algunos lenguajes, debe especificar un *archivo de inicio* válido en el código base, como un script, archivo ejecutable o proyecto. El cuadro de lista desplegable situado junto al botón **Inicio** de la barra de herramientas muestra todos los elementos de inicio que Visual Studio detecta, así como los elementos que designa específicamente. Visual Studio ejecuta este código primero al depurar el código.

La configuración del código que se ejecuta en Visual Studio difiere en función del tipo de código del que se trata y cuáles son las herramientas de compilación.

### <a name="codebases-that-use-msbuild"></a>Códigos base que usan MSBuild

Los códigos base basados en MSBuild pueden tener varias configuraciones de compilación que aparecen en la lista desplegable del botón **Inicio**. Seleccione el archivo que desea usar como el elemento de inicio y, luego, elija el botón **Inicio** para comenzar con la depuración.

> [!NOTE]
> En el caso de los códigos base de C# y Visual Basic, debe tener instalada la carga de trabajo **Desarrollo para el escritorio de .NET**. En el caso de los códigos base de C++, debe tener instalada la carga de trabajo **Desarrollo para el escritorio con C++** .

### <a name="codebases-that-use-custom-build-tools"></a>Bases de código que usan herramientas de compilación personalizadas

Si el código base usa las herramientas de compilación personalizadas, debe indicarle a Visual Studio cómo compilar el código con las *tareas de compilación* que se definen en un archivo *.json*. Para más información, consulte [Personalización de las tareas de compilación y depuración](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

### <a name="codebases-that-contain-python-or-javascript-code"></a>Códigos base que contienen código de Python o JavaScript

Si el código base contiene código de Python o JavaScript, no es necesario configurar ningún archivo *.json*, pero sí debe instalar la carga de trabajo correspondiente. También debe configurar el script de inicio:

1. Instale la carga de trabajo [Desarrollo de Node.js](https://visualstudio.microsoft.com/vs/node-js/) o [Desarrollo de Python](https://visualstudio.microsoft.com/vs/python/) mediante la elección de **Herramientas** > **Obtener herramientas y características** o mediante el cierre de Visual Studio y posterior ejecución del Instalador de Visual Studio.

   ![Cargas de trabajo de desarrollo de Node.js y Python](media/python_nodejs_workloads.png)

1. En el **Explorador de soluciones**, en el menú contextual o con un clic con el botón derecho en un archivo JavaScript o Python, elija el comando **Establecer como elemento de inicio**.

1. Elija el botón **Inicio** para comenzar la depuración.

### <a name="codebases-that-contain-c-code"></a>Códigos base que contienen código C++

Para información sobre cómo abrir el código C++ sin soluciones ni proyectos en Visual Studio, consulte [Open Folder projects for C++](/cpp/build/open-folder-projects-cpp) (Proyectos Abrir carpeta para C++).

### <a name="codebases-that-contain-a-visual-studio-project"></a>Códigos base que contienen un proyecto de Visual Studio

Si la carpeta de código contiene un proyecto de Visual Studio, puede designar el proyecto como el elemento de inicio.

![Establecimiento del proyecto como elemento de inicio](media/customize-set-project-as-startup-item.png)

El texto del botón **Inicio** cambia para reflejar que el proyecto es el elemento de inicio.

![Proyecto en el botón Inicio](media/customize-start-button-project.png)

## <a name="see-also"></a>Vea también

- [Personalización de las tareas de compilación y depuración](../ide/customize-build-and-debug-tasks-in-visual-studio.md)
- [Open Folder projects for C++](/cpp/build/open-folder-projects-cpp) (Proyectos Abrir carpeta para C++)
- [CMake projects in C++](/cpp/build/cmake-projects-in-visual-studio) (Proyectos CMake en C++)
- [Escribir código en el editor de código y texto](../ide/writing-code-in-the-code-and-text-editor.md)
