---
title: "Cómo: extensiones de ida y vuelta para Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 06/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
caps.latest.revision: "1"
author: willbrown
ms.author: willbrown
manager: justinclareburt
ms.workload: willbrown
ms.openlocfilehash: e6ce654e158fbfbdaa3692d37f638e72085f8c4c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>Cómo: crear extensiones compatibles con 2017 de Visual Studio y Visual Studio 2015

Este documento explica cómo crear proyectos de extensibilidad de ida y vuelta entre Visual Studio 2015 y Visual Studio de 2017. Después de completar esta actualización, un proyecto podrán abrir, compilar, instalar y ejecutar en Visual Studio 2015 y Visual Studio de 2017.  Como referencia, encontrará algunas extensiones que pueden ida y vuelta entre Visual Studio 2015 y Visual Studio de 2017 [aquí](https://github.com/Microsoft/VSSDK-Extensibility-Samples) en los ejemplos de extensibilidad de Microsoft.

Si solo desea compilar en Visual Studio de 2017, pero desea que la salida VSIX para que se ejecute en Visual Studio 2015 y Visual Studio de 2017, a continuación, hacer referencia a la [documento de migración de extensión](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

>**Nota:** debido a cambios en Visual Studio entre las versiones, algunas cosas que ha trabajado en una versión no funcionará otro. Asegúrese de que las características que está intentando tener acceso están disponibles en ambas versiones o la extensión tendrá resultados inesperados.

Este es un resumen de los pasos que puede completar en este documento a un VSIX de ida y vuelta:

1. Importar paquetes de NuGet correctos.
2. Actualice el manifiesto de la extensión:
    * Destino de instalación
    * Requisitos previos
3. Actualizar CSProj:
    * Actualización `<MinimumVisualStudioVersion>`.
    * Agregar el `<VsixType>` propiedad.
    * Agregue la propiedad depuración `($DevEnvDir)` 3 veces.
    * Agregar condiciones para la importación de herramientas de compilación y los destinos.

4. Compilar y probar

## <a name="environment-setup"></a>Configuración de entorno

Este documento se da por supuesto que tiene instalado en su equipo lo siguiente:

* Visual Studio 2015 con instalado el SDK de VS
* 2017 de Visual Studio con la carga de trabajo de extensibilidad instalado

## <a name="recommended-approach"></a>Enfoque recomendado

Se recomienda iniciar esta actualización con Visual Studio 2015, en lugar de 2017 de Visual Studio. La principal ventaja del desarrollo en Visual Studio 2015 es asegurarse de que no hacer referencia a ensamblados que no están disponibles en Visual Studio 2015. Si lo hace el desarrollo en Visual Studio de 2017, se corre el riesgo que podrían introducir una dependencia en un ensamblado que solo existe en Visual Studio de 2017.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Asegúrese de que no hay ninguna referencia a project.json

Más adelante en este documento, se insertará instrucciones de importación condicionales en el archivo *.csproj.  Esto no funcionará si las referencias de NuGet se almacenan en project.json. Por lo tanto, se recomienda para mover todas las referencias de NuGet en el archivo packages.config.
Si el proyecto contiene un archivo project.json:

* Tome nota de las referencias en project.json.
* En el Explorador de soluciones, elimine el archivo project.json desde el proyecto.
    * Esto eliminará el archivo project.json y quitarlo del proyecto.
* Agregue que las referencias de NuGet a registrar en el proyecto.
    * Haga doble clic en la solución y elija **administrar paquetes de NuGet para la solución...**
    * Visual Studio crea automáticamente el archivo packages.config para usted

>**Nota:** si el proyecto contiene paquetes EnvDTE, necesite agregar haciendo clic en **referencias** seleccionar **Agregar referencia** y agregar la referencia adecuada.  Con paquetes de NuGet, puede crear errores al intentar compilar el proyecto.

## <a name="adding-appropriate-build-tools"></a>Agregar herramientas de compilación adecuados

Para asegurarse de que necesitamos agregar herramientas de compilación que nos permitirá compilar y depurar de forma adecuada. Microsoft ha creado un ensamblado para esta llamada Microsoft.VisualStudio.Sdk.BuildTasks.

Para compilar e implementar un VSIXv3 en Visual Studio 2015 y 2017, necesitará los siguientes paquetes de NuGet:

Versión | Herramientas integradas
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

Para ello:

* Agregue el paquete de NuGet Microsoft.VisualStudio.Sdk.BuildTasks.14.0 al proyecto.
* Si el proyecto no contiene Microsoft.VSSDK.BuildTools, agréguela.
* Asegúrese de que la versión de Microsoft.VSSDK.BuildTools es 15.x o superior.

## <a name="update-extension-manifest"></a>Actualizar el manifiesto de la extensión

### <a name="1-installation-targets"></a>1. Destinos de instalación

Es necesario indicar a Visual Studio qué versiones de destino para la creación de una extensión VSIX.  Normalmente, estas referencias están en versión 14.0 (Visual Studio 2015) o versión 15.0 (Visual Studio 2017).  En nuestro caso, deseamos compilar un VSIX que va a instalar una extensión en ambos casos, por lo que necesitamos a ambas versiones de destino.  Si desea que su VSIX para crear e instalar en versiones anteriores a 14.0, puede hacerlo estableciendo el número de versión anterior; Sin embargo, la versión 10.0 y versiones anterior ya no se admiten.

* Abra el archivo source.extension.vsixmanifest en Visual Studio.
* Abra la **destinos de instalación** ficha.
* Cambiar el **intervalo de versiones** a [14,0, 16,0).  El ' [' indica a Visual Studio para incluir 14,0 y todas las versiones más allá de él.  El ')' indica a Visual Studio para incluir todas las versiones de 15.0 hacia arriba, pero no incluyen versión 16.0.
* Guarde todos los cambios y cierre todas las instancias de Visual Studio.

![Imagen de destinos de instalación](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. Agregar requisitos previos para el archivo extension.vsixmanifest

Requisitos previos son una nueva característica de Visual Studio de 2017.  En este caso, el Editor de Visual Studio Core es necesario como requisito previo. Puesto que el Diseñador de Visual Studio 2015 VSIX no controla el nuevo `Prerequisites` sección, tendrá que editar este elemento manualmente en el código XML.  Como alternativa, puede abrir Visual Studio de 2017 y usar el Diseñador de manifiestos actualizado para insertar los requisitos previos.

Para hacerlo manualmente:

* Navegue hasta el directorio del proyecto en Explorador de archivos.
* Abra el `extension.vsixmanifest` archivo con un editor de texto.
* Agregue la siguiente etiqueta:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Guarde y cierre el archivo.

>**Nota:** si decide realizar esto con el diseñador VSIX en Visual Studio de 2017, debe editar manualmente la versión de requisitos previos para asegurarse de que es compatible con todas las versiones de Visual Studio de 2017.  Esto es porque el diseñador, inserta la versión mínima como su versión actual de Visual Studio (por ejemplo, 15.0.26208.0).  Sin embargo, dado que otros usuarios pueden tener una versión anterior, deberá editar manualmente este a 15.0.

En este momento, el archivo de manifiesto debe tener un aspecto similar al siguiente:

![Ejemplo de los requisitos previos](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Modificar el archivo de proyecto (myproject.csproj)

Se recomienda tener una referencia a una modificación .csproj abierto mientras realiza este paso.  Puede encontrar varios ejemplos [aquí](https://github.com/Microsoft/VSSDK-Extensibility-Samples).  Seleccione cualquier ejemplo de extensibilidad, busque el archivo .csproj como referencia y ejecutar los siguientes pasos:

* Navegue hasta el directorio del proyecto en Explorador de archivos.
* Abra el archivo myproject.csproj con un editor de texto.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. Actualizar la MinimumVisualStudioVersion

* Establece la versión de mínimo de visual studio en `$(VisualStudioVersion)` y agregue una instrucción condicional para él.  Agregue estas etiquetas si no existen.  Asegúrese de que las etiquetas se establecen como sigue:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. Agregue la propiedad VsixType

* Agregue la siguiente etiqueta `<VsixType>v3</VsixType>` a un grupo de propiedades.

>**Nota:** se recomienda agregar esto a continuación la `<OutputType></OutputType>` etiqueta.

### <a name="3-add-the-debugging-properties"></a>3. Agregar las propiedades de depuración

* Agregue el siguiente grupo de propiedades:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Eliminar todas las instancias de las acciones siguientes en el archivo .csproj y cualquier. csproj.user archivos:

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. Agregar condiciones a las importaciones de herramientas de compilación

* Agregar instrucciones condicionales adicionales a la `<import>` etiquetas que tengan una referencia Microsoft.VSSDK.BuildTools.  Hacer esto mediante la inserción de `'$(VisualStudioVersion)' != '14.0' And` al principio de la instrucción de condición.  Estas instrucciones aparecerán en el encabezado y pie de página del archivo csproj.

Por ejemplo:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201… Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…/>
```

* Agregar instrucciones condicionales adicionales a la `<import>` etiquetas que tengan un Microsoft.VisualStudio.Sdk.BuildTasks.14.0.  Hacer esto mediante la inserción de `'$(VisualStudioVersion)' == '14.0' And` al principio de la instrucción de condición. Estas instrucciones aparecerán en el encabezado y pie de página del archivo csproj.

Por ejemplo:

```xml
<Import Project="packages\ Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0… Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…/>
```

* Agregar instrucciones condicionales adicionales a la `<Error>` etiquetas que tengan una referencia Microsoft.VSSDK.BuildTools.  Hacer esto mediante la inserción de `'$(VisualStudioVersion)' != '14.0' And` al principio de la instrucción de condición. Estas instrucciones aparecerán en el pie de página del archivo csproj.

Por ejemplo:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…/>
```

* Agregar instrucciones condicionales adicionales a la `<Error>` etiquetas que tengan un Microsoft.VisualStudio.Sdk.BuildTasks.14.0.  Hacer esto mediante la inserción de `'$(VisualStudioVersion)' == '14.0' And` al principio de la instrucción de condición. Estas instrucciones aparecerán en el pie de página del archivo csproj.

Por ejemplo:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\ Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…/>
```

* Guarde el archivo csproj y ciérrelo.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>Probar la instalación de la extensión de Visual Studio 2015 y Visual Studio de 2017

En este momento, el proyecto estará preparado para compilar un VSIXv3 que puede instalar en Visual Studio 2015 y Visual Studio de 2017.

* Abra el proyecto en Visual Studio 2015
* Compilar el proyecto y confirmar en la salida que se compila correctamente; una extensión VSIX
* Navegue hasta el directorio del proyecto
* Abra la Papelera -> carpeta de depuración
* Haga doble clic en el archivo VSIX e instalar la extensión en Visual Studio 2015 y Visual Studio de 2017
* Asegúrese de que puede ver la extensión en Herramientas -> extensiones y actualizaciones en la sección "Instalar".
* Intento de ejecución o usar la extensión para comprobar que funciona

![Buscar una extensión VSIX](media/finding-a-VSIX-example.png)

>**Nota:** si el proyecto se bloquea con el mensaje "abrir el archivo" fuerza que cerrar Visual Studio, navegue hasta el directorio del proyecto, mostrar las carpetas ocultas y elimine la carpeta VS.
