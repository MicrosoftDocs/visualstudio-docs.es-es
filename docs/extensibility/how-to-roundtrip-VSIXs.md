---
title: Cómo las extensiones de ida y vuelta
ms.date: 06/25/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: gregvanl
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: 826089f1018bc6156cd49bab3afb19e7bb34a47d
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750737"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>Cómo: crear extensiones compatibles con Visual Studio 2017 y Visual Studio 2015

Este documento explica cómo crear proyectos de extensibilidad de ida y vuelta entre Visual Studio 2015 y Visual Studio 2017. Después de completar esta actualización, será capaz de abrir, compilar, instalar y ejecutar en Visual Studio 2015 y Visual Studio 2017 en un proyecto. Como referencia, algunas extensiones que pueden ida y vuelta entre Visual Studio 2015 y Visual Studio 2017 pueden encontrarse en el [ejemplos de extensibilidad de SDK de VS](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Si solo desea compilar en Visual Studio 2017, pero desea que la salida VSIX para ejecutar en Visual Studio 2015 y Visual Studio 2017, a continuación, hacer referencia a la [documento de migración de extensión](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

> [!NOTE]
> Debido a los cambios entre las versiones en Visual Studio, algunas cosas que funcionaban en una versión no funcionan en otro. Asegurarse de que están disponibles en las versiones de las características que está intentando acceder o la extensión tendrá resultados inesperados.

Este es un esquema de los pasos que puede completar en este documento a un archivo VSIX de ida y vuelta:

1. Importar paquetes de NuGet correctos.
2. Actualice el manifiesto de la extensión:
    * Destino de instalación
    * Requisitos previos
3. Actualizar CSProj:
    * Actualización `<MinimumVisualStudioVersion>`.
    * Agregar el `<VsixType>` propiedad.
    * Agregue la propiedad de depuración `($DevEnvDir)` 3 veces.
    * Agregar condiciones para la importación de las herramientas de compilación y destinos.

4. Compilación y prueba

## <a name="environment-setup"></a>Configuración del entorno

Este documento se supone que tiene instalados en el equipo de los siguientes elementos:

* Visual Studio 2015 con el SDK de VS instalados
* Visual Studio 2017 con la carga de trabajo de extensibilidad instalado

## <a name="recommended-approach"></a>Enfoque recomendado

Se recomienda iniciar esta actualización con Visual Studio 2015, en lugar de Visual Studio 2017. La principal ventaja de desarrollar con Visual Studio 2015 es para asegurarse de que no hace referencia a ensamblados que no están disponibles en Visual Studio 2015. Si lo hace el desarrollo en Visual Studio 2017, hay un riesgo que podrían introducir una dependencia en un ensamblado que solo existe en Visual Studio 2017.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Asegúrese de que no hay ninguna referencia de project.json

Más adelante en este documento, se insertará instrucciones de importación condicional en para su **.csproj* archivo.  Esto no funcionará si se almacenan las referencias de NuGet en *project.json*. Por lo tanto, se recomienda para mover todas las referencias de NuGet para la *packages.config* archivo.
Si el proyecto contiene un *project.json* archivo:

* Tome nota de las referencias de *project.json*.
* Desde el **el Explorador de soluciones**, elimine el *project.json* archivo del proyecto. Esto elimina la *project.json* de archivo y lo quita del proyecto.
* Agregue que las referencias de NuGet de nuevo al proyecto:
    * Haga doble clic en el **solución** y elija **administrar paquetes de NuGet para la solución**.
    * Visual Studio crea automáticamente la *packages.config* archivo automáticamente.

> [!NOTE]
> Si el proyecto contenía paquetes EnvDTE, deba agregarse, haga clic con el botón secundario en **referencias** seleccionando **Agregar referencia** y agregar la referencia correspondiente.  Uso de paquetes NuGet, puede crear errores al intentar compilar el proyecto.

## <a name="add-appropriate-build-tools"></a>Agregar herramientas de compilación adecuado

Para asegurarse de que necesitamos agregar herramientas de compilación que nos permitirá crear y depurar de forma adecuada. Microsoft ha creado un ensamblado para esta llamada Microsoft.VisualStudio.Sdk.BuildTasks.

Para compilar e implementar un VSIXv3 en Visual Studio 2015 y 2017, necesita los siguientes paquetes NuGet:

Versión | Herramientas integradas
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

Para ello:

* Agregue el paquete de NuGet Microsoft.VisualStudio.Sdk.BuildTasks.14.0 al proyecto.
* Si el proyecto no contiene Microsoft.VSSDK.BuildTools, agréguelo.
* Asegúrese de que la versión de Microsoft.VSSDK.BuildTools es 15.x o superior.

## <a name="update-extension-manifest"></a>Actualizar el manifiesto de extensión

### <a name="1-installation-targets"></a>1. Destinos de instalación

Es necesario indicar a Visual Studio qué versiones de destino para la creación de un archivo VSIX.  Normalmente, estas referencias son a la versión 14.0 (Visual Studio 2015) o versión 15.0 (Visual Studio 2017).  En nuestro caso, deseamos crear un VSIX que se instalará una extensión en ambos casos, por lo que necesitamos para ambas versiones de destino.  Si desea que el proyecto de VSIX para crear e instalar en versiones anteriores a 14.0, esto puede hacerse estableciendo el número de versión anterior; Sin embargo, ya no se admite la versión 10.0 y versiones anterior.

* Abra el *source.extension.vsixmanifest* archivo en Visual Studio.
* Abra el **destinos de instalación** ficha.
* Cambiar el **intervalo de versiones** a [14,0, 16.0).  El ' [' indica a Visual Studio para incluir 14,0 y todas las versiones anteriores se.  El ')' indica a Visual Studio para incluir todas las versiones de 15.0 hacia arriba, pero no incluyen la versión 16.0.
* Guarde todos los cambios y cierre todas las instancias de Visual Studio.

![Imagen de instalación de destinos](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. Agregar requisitos previos para la *extension.vsixmanifest* archivo

Requisitos previos son una característica nueva con Visual Studio 2017.  En este caso, el Editor de núcleo de Visual Studio es necesario como requisito previo. Puesto que el Diseñador de Visual Studio 2015 VSIX no controla el nuevo `Prerequisites` sección, deberá modificar esta parte manualmente en el código XML.  Como alternativa, puede abrir Visual Studio 2017 y utilizar el Diseñador de manifiestos actualizado para insertar los requisitos previos.

Para hacerlo manualmente:

* Navegue al directorio del proyecto en el Explorador de archivos.
* Abra el *extension.vsixmanifest* archivo con un editor de texto.
* Agregue la siguiente etiqueta:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Guarde y cierre el archivo.

> [!NOTE]
> Si decide realizar esto con el diseñador VSIX en Visual Studio 2017, deberá editar manualmente la versión de requisitos previos para asegurarse de que es compatible con todas las versiones de Visual Studio 2017.  Esto es porque el diseñador, inserta la versión mínima como la versión actual de Visual Studio (por ejemplo, 15.0.26208.0).  Sin embargo, dado que otros usuarios tengan una versión anterior, le interesará editar manualmente este 15.0.

En este momento, el archivo de manifiesto debe tener un aspecto similar al siguiente:

![Ejemplo de los requisitos previos](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Modificar el archivo de proyecto (myproject.csproj)

Se recomienda tener una referencia a una modificación .csproj abierto mientras realiza este paso.  Puede encontrar varios ejemplos [aquí](https://github.com/Microsoft/VSSDK-Extensibility-Samples).  Seleccione cualquier ejemplo de extensibilidad, busque el *.csproj* como referencia de archivo y ejecute los siguientes pasos:

* Vaya al directorio del proyecto en **Explorador de archivos**.
* Abra el *myproject.csproj* archivo con un editor de texto.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. Actualizar el MinimumVisualStudioVersion

* Establece la versión mínima de visual studio en `$(VisualStudioVersion)` y agregue una instrucción condicional para ella.  Agregue estas etiquetas si no existen.  Asegúrese de que las etiquetas se establecen como sigue:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. Agregue la propiedad VsixType.

* Agregue la siguiente etiqueta `<VsixType>v3</VsixType>` a un grupo de propiedades.

> [!NOTE]
> Se recomienda agregar esto a continuación el `<OutputType></OutputType>` etiqueta.

### <a name="3-add-the-debugging-properties"></a>3. Agregar las propiedades de depuración

* Agregue el siguiente grupo de propiedades:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Eliminar todas las instancias del siguiente ejemplo de código desde el *.csproj* archivo y cualquier *. csproj.user* archivos:

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. Agregar condiciones a las importaciones de las herramientas de compilación

* Agregar instrucciones condicionales adicionales a la `<import>` etiquetas que tienen una referencia Microsoft.VSSDK.BuildTools.  Insertar `'$(VisualStudioVersion)' != '14.0' And` en la parte delantera de la instrucción de condición.  Estas instrucciones aparecerán en el encabezado y pie de página del archivo csproj.

Por ejemplo:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* Agregar instrucciones condicionales adicionales a la `<import>` etiquetas que tienen un Microsoft.VisualStudio.Sdk.BuildTasks.14.0. Insertar `'$(VisualStudioVersion)' == '14.0' And` en la parte delantera de la instrucción de condición. Estas instrucciones aparecerán en el encabezado y pie de página del archivo csproj.

Por ejemplo:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Agregar instrucciones condicionales adicionales a la `<Error>` etiquetas que tienen una referencia Microsoft.VSSDK.BuildTools.  Hacer esto mediante la inserción de `'$(VisualStudioVersion)' != '14.0' And` en la parte delantera de la instrucción de condición. Estas instrucciones se mostrarán en el pie de página del archivo csproj.

Por ejemplo:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* Agregar instrucciones condicionales adicionales a la `<Error>` etiquetas que tienen un Microsoft.VisualStudio.Sdk.BuildTasks.14.0.  Insertar `'$(VisualStudioVersion)' == '14.0' And` en la parte delantera de la instrucción de condición. Estas instrucciones se mostrarán en el pie de página del archivo csproj.

Por ejemplo:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Guarde el archivo csproj y ciérrelo.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>Probar las instalaciones de extensión en Visual Studio 2015 y Visual Studio 2017

En este momento, el proyecto debería estar listo para compilar un VSIXv3 que puede instalar en Visual Studio 2015 y Visual Studio 2017.

* Abra el proyecto en Visual Studio 2015.
* Compile el proyecto y confirmar en la salida que se compila correctamente un archivo VSIX.
* Navegue al directorio del proyecto.
* Abra el *\bin\Debug* carpeta.
* Haga doble clic en el archivo VSIX e instale la extensión en Visual Studio 2015 y Visual Studio 2017.
* Asegúrese de que puede ver la extensión en **herramientas** > **extensiones y actualizaciones** en el **instalado** sección.
* Intento de ejecución o usar la extensión para comprobar que funciona.

![Buscar un archivo VSIX](media/finding-a-VSIX-example.png)

> [!NOTE]
> Si el proyecto se bloquea con el mensaje **al abrir el archivo**, Forzar cierre Visual Studio, vaya al directorio del proyecto, mostrar las carpetas ocultas y eliminar el *.vs* carpeta.