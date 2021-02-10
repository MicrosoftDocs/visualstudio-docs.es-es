---
title: Procedimientos para ejecutar un programa (C#)
description: Guía para principiantes sobre cómo ejecutar un programa de C# en Visual Studio.
ms.custom: get-started
ms.date: 10/16/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bbebcec3f5b2de01bcbfa7839f68e6f7a3e2cc64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922847"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>Procedimiento Ejecución de un programa de C# en Visual Studio

Lo que necesita hacer para ejecutar un programa depende del punto de partida, del tipo de programa, aplicación o servicio, y de si quiere que se ejecute en el depurador o no. En el caso más simple, si tiene un proyecto abierto en Visual Studio, puede compilarlo y ejecutarlo presionando **Ctrl**+**F5** (**Iniciar sin depurar**) o **F5** (**Iniciar con depuración**), o bien presionando la flecha de color verde (**botón Iniciar**) de la barra de herramientas principal de Visual Studio.

![Captura de pantalla en la que se muestra el botón Iniciar](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>Inicio a partir de un proyecto

Si tiene un proyecto de C# (archivo *.csproj*), puede ejecutarlo si es un programa ejecutable. Si un proyecto contiene un archivo de C# con un método `Main` y su resultado es un ejecutable (EXE), lo más probable es que se ejecute si se compila correctamente.

Si ya tiene el código del programa en un proyecto de Visual Studio, abra el proyecto. Para abrir el proyecto, haga doble clic o pulse en el archivo *.csproj* desde el Explorador de archivos de Windows o, en Visual Studio, elija **Abrir un proyecto**, busque el archivo de proyecto ( *.csproj*) y selecciónelo.

Una vez que se carguen los proyectos en Visual Studio, presione **Ctrl**+**F5** (**Iniciar sin depurar**) o use el botón **Iniciar** de color verde de la barra de herramientas de Visual Studio para ejecutar el programa.  Si hay varios proyectos, el que tenga el método `Main` se debe establecer como proyecto de inicio. Para establecer el proyecto de inicio, haga clic con el botón derecho en un nodo de proyecto y elija **Establecer como proyecto de inicio**.

![Establecimiento del proyecto de inicio](media/set-as-startup-project.png)

Visual Studio intenta compilar y ejecutar el proyecto.  Si hay errores de compilación, verá el resultado de la compilación en la ventana **Salida** y los errores en la ventana **Lista de errores**.

Si la compilación se realiza correctamente, la aplicación se ejecutará de la forma adecuada para el tipo de proyecto. Las aplicaciones de consola se ejecutan en una ventana de terminal, las de escritorio de Windows se inician en una ventana nueva, las aplicaciones web se inician en el explorador (hospedado por IIS Express), etc.

## <a name="starting-from-code"></a>Inicio a partir de código

Si va a empezar a partir de un listado de código, un archivo de código o un número pequeño de archivos, asegúrese primero de que el código que quiere ejecutar proviene de un origen de confianza y es un programa ejecutable. Si tiene un método `Main`, es probable que esté pensado como un programa ejecutable en el que puede usar la plantilla Aplicación de consola para crear un proyecto con el fin de trabajar con él en Visual Studio.

### <a name="code-listing-for-a-single-file"></a>Listado de código para un solo archivo

Inicie Visual Studio, abra un proyecto de consola de C# vacío, seleccione todo el código en el archivo .cs que ya está en el proyecto y elimínelo. Después, pegue el contenido del código en el archivo .cs. Al pegar el código, sobrescriba o elimine el código que había antes. Cambie el nombre del archivo para que coincida con el código original.

### <a name="code-listings-for-a-few-files"></a>Listados de código para varios archivos

Inicie Visual Studio, abra un proyecto de consola de C# vacío, seleccione todo el código en el archivo .cs que ya está en el proyecto y elimínelo. Después, pegue el contenido del primer archivo de código en el archivo .cs. Cambie el nombre del archivo para que coincida con el código original. 

Para un segundo archivo, haga clic con el botón derecho en el nodo del proyecto en el **Explorador de soluciones** para abrir el menú contextual del proyecto y elija **Agregar > Elemento existente** (o bien use la combinación de teclado **Mayús**+**Alt**+**A**) y seleccione los archivos de código.

### <a name="multiple-files-on-disk"></a>Varios archivos en disco

1. Cree un proyecto del tipo adecuado (use **Aplicación de consola** de C# si no está seguro).

2. Haga clic con el botón derecho en el nodo del proyecto y elija **Agregar** > **Elemento existente** para seleccionar los archivos e importarlos en el proyecto.  

### <a name="starting-from-a-folder"></a>Inicio a partir de una carpeta

Cuando trabaje con una carpeta de muchos archivos, compruebe primero si hay un proyecto o una solución.  Si el programa se ha creado con Visual Studio, debe buscar un archivo de proyecto o de solución. Busque archivos con las extensiones *.csproj* o .sln, y en el Explorador de archivos de Windows haga doble clic en uno de ellos para abrirlos en Visual Studio. Vea [Inicio a partir de una solución o un proyecto de Visual Studio](#starting-from-a-project).

Si no tiene un archivo de proyecto, por ejemplo, si el código se ha desarrollado en otro entorno, abra la carpeta de nivel superior con el método **Abrir carpeta** en Visual Studio. Vea [Desarrollo de código sin proyectos o soluciones](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="starting-from-a-github-or-azure-devops-repo"></a>Inicio desde un repositorio de GitHub o Azure DevOps

Si el código que quiere ejecutar está en un repositorio de GitHub o de Azure DevOps, puede usar Visual Studio para abrir el proyecto directamente desde el repositorio. Vea [Apertura de un proyecto desde un repositorio](../tutorial-open-project-from-repo.md).

## <a name="run-the-program"></a>Ejecutar el programa

Para iniciar el programa, presione la flecha de color verde (**botón Iniciar**) de la barra de herramientas principal de Visual Studio, o bien presione **F5** o **Ctrl**+**F5** para ejecutar el programa. Cuando se usa el botón **Iniciar**, se ejecuta en el depurador.  Visual Studio intenta compilar el código del proyecto y ejecutarlo.  Si la operación se realiza correctamente, perfecto. En caso contrario, siga leyendo para obtener algunas ideas sobre cómo conseguir que se compile de forma correcta.

## <a name="troubleshooting"></a>Solución de problemas

Es posible que el código tenga errores, pero si es correcto y solo depende de otros ensamblados o paquetes NuGet, o bien se ha escrito para tener como destino otra versión de .NET, es posible que lo pueda corregir fácilmente.

### <a name="add-references"></a>Agregar referencias

Para que se compile de la forma adecuada, el código debe ser correcto y tener las referencias adecuadas configuradas en bibliotecas u otras dependencias. Puede examinar las líneas onduladas de color rojo y la **Lista de errores** para ver si el programa tiene algún error, incluso antes de compilarlo y ejecutarlo. Si ve errores relacionados con nombres sin resolver, es probable que tenga agregar una referencia o una directiva using, o las dos. Si el código hace referencia a ensamblados o paquetes NuGet, tendrá que agregar esas referencias en el proyecto.

Visual Studio intenta ayudarle a identificar las referencias que faltan. Cuando hay un nombre sin resolver, aparece un icono de bombilla en el editor. Si hace clic en la bombilla, puede ver algunas sugerencias sobre cómo corregir el problema. Las correcciones pueden ser las siguientes:

- agregar una directiva using
- agregar una referencia a un ensamblado
- instalar un paquete NuGet

#### <a name="missing-using-directive"></a>Directiva using no disponible

Por ejemplo, en la pantalla siguiente, puede optar por agregar `using System;` al inicio del archivo de código para resolver el nombre sin resolver `Console`:

![Captura de pantalla de la bombilla para agregar una directiva using](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>Referencia de ensamblado que falta

Las referencias de .NET pueden tener el formato de ensamblados o paquetes NuGet. Normalmente, si encuentra código fuente, el publicador o el autor explicarán los ensamblados que se necesitan y los paquetes de los que depende el código. Para agregar manualmente una referencia a un proyecto, haga clic con el botón derecho en el nodo **Referencias** en el **Explorador de soluciones**, elija **Agregar referencia** y busque el ensamblado necesario.

![Captura de pantalla del menú Agregar referencia](media/add-reference.png)

Puede buscar ensamblados y agregar referencias siguiendo las instrucciones de [Adición o eliminación de referencias con el Administrador de referencias](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

#### <a name="missing-nuget-package"></a>Paquete NuGet no disponible

Si Visual Studio detecta que falta un paquete NuGet, aparece una bombilla y le ofrece la opción de instalarlo:

![Captura de pantalla de la bombilla para instalar el paquete](media/lightbulb-add-package.png)

Si eso no soluciona el problema y Visual Studio no encuentra el paquete, intente buscarlo en línea. Vea [Instalación y uso de un paquete NuGet en Visual Studio](/nuget/quickstart/install-and-use-a-package-in-visual-studio).

## <a name="use-the-right-version-of-net"></a>Uso de la versión correcta de .NET

Como las distintas versiones de .NET Framework tienen cierto grado de compatibilidad con versiones anteriores, un marco de trabajo más reciente podría ejecutar código escrito para un marco anterior sin modificaciones. Sin embargo, en ocasiones es necesario tener como destino un marco específico. Es posible que tenga que instalar una versión específica de .NET Framework o .NET Core, si todavía no está instalada. Vea [Modificación de Visual Studio](../../install/modify-visual-studio.md).

Para cambiar la plataforma de destino, vea [Cambio del marco de destino](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version). Para más información, vea [Solución de problemas de versión de .NET Framework de destino](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="next-steps"></a>Pasos siguientes

Explore el entorno de desarrollo de Visual Studio; para ello, lea [Le damos la bienvenida al IDE de Visual Studio](../visual-studio-ide.md).

## <a name="see-also"></a>Vea también

[Creación de la primera aplicación de C#](tutorial-console.md)
