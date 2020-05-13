---
title: Actualizar plantillas de proyecto y elemento personalizadas para Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 5f807e142b376d05e5a44600e8f6b24ddb3593be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698860"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Actualizar plantillas personalizadas de proyecto y elemento para Visual Studio 2017

A partir de Visual Studio 2017, Visual Studio detecta plantillas de proyecto y elemento que se han instalado mediante un .vsix o un .msi de una manera diferente a las versiones anteriores de Visual Studio. Si tiene extensiones que usan plantillas de proyecto o elemento personalizadas, debe actualizar las extensiones. En este artículo se explica lo que debe hacer.

Este cambio solo afecta a Visual Studio 2017. No afecta a versiones anteriores de Visual Studio.

Si desea crear un proyecto o una plantilla de elemento como parte de una extensión VSIX, consulte Creación de plantillas de [proyecto y elemento personalizadas](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Escaneo de plantillas

En versiones anteriores de Visual Studio, **devenv /setup** o **devenv /installvstemplates** examinaban el disco local para buscar plantillas de proyecto y elemento. A partir de Visual Studio 2017, el análisis se realiza solo para la ubicación de nivel de usuario. La ubicación de nivel de usuario predeterminada es **%USERPROFILE%-Documents\\<versión\>\\**de Visual Studio . Esta ubicación se usa para las plantillas generadas por **el** > comando Plantillas de exportación de**proyectos...,** si la opción **Importar automáticamente la plantilla en Visual Studio** está seleccionada en el asistente.

Para otras ubicaciones (no de usuario), debe incluir un archivo manifest(.vstman) que especifique la ubicación y otras características de la plantilla. El archivo .vstman se genera junto con el archivo .vstemplate utilizado para las plantillas. Si instala la extensión con un .vsix, puede hacerlo volviendo a compilar la extensión en Visual Studio 2017. Pero si utiliza un archivo .msi, debe realizar los cambios manualmente. Para obtener una lista de lo que debe hacer para realizar estos cambios, consulte **Actualizaciones de extensiones instaladas con un archivo . MSI** más adelante en esta página.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Cómo actualizar una extensión VSIX con plantillas de proyecto o elemento

1. Abra la solución en Visual Studio 2017. Se le pedirá que actualice el código. Haga clic en **OK**.

2. Una vez completada la actualización, es posible que deba cambiar la versión del destino de instalación. En el proyecto VSIX, abra el archivo source.extension.vsixmanifest y seleccione la pestaña **Install Targets.** Si el campo Intervalo de **versiones** es **[14.0]**, haga clic en **Editar** y cámbielo para incluir Visual Studio 2017. Por ejemplo, puede establecerlo en **[14.0,15.0]** para instalar la extensión en Visual Studio 2015 o Visual Studio 2017, o en **[15.0]** para instalarla solo en Visual Studio 2017.

3. Vuelva a compilar el código.

4. Cierre Visual Studio.

5. Instale el VSIX.

6. Puede probar la actualización haciendo lo siguiente:

    1. El cambio de análisis de archivos se activa mediante la siguiente clave del Registro:

         **reg add hklm-software-microsoft-visualstudio-15.0-VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**

    2. Después de agregar la clave, ejecute **devenv /installvstemplates**.

    3. Vuelva a abrir Visual Studio. Debe encontrar la plantilla en la ubicación esperada.

    > [!NOTE]
    > Las plantillas de proyecto de extensibilidad de Visual Studio no están disponibles cuando la clave del Registro está presente. Debe eliminar la clave del Registro (y volver a ejecutar **devenv /installvstemplates**) para usarlas.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Otras recomendaciones para implementar plantillas de proyectos y elementos

- Evite el uso de archivos de plantilla comprimidos. Los archivos de plantilla comprimidos deben descomprimirse para recuperar recursos y contenido, por lo que serán más costosos de usar. En su lugar, debe implementar plantillas de proyecto y elemento como archivos individuales en su propio directorio para acelerar la inicialización de plantillas. Para las extensiones VSIX, las tareas de compilación del SDK descomprimirán automáticamente cualquier plantilla comprimida al crear el archivo VSIX.

- Evite utilizar entradas de ID de paquete/recurso para el nombre de la plantilla, la descripción, el icono o la vista previa para evitar cargas innecesarias del ensamblado de recursos durante la detección de plantillas. En su lugar, puede usar manifiestos localizados para crear una entrada de plantilla para cada configuración regional, que usa nombres o propiedades localizadas.

- Si incluye plantillas como elementos de archivo, es posible que la generación de manifiestos no proporcione los resultados esperados. En ese caso, tendrá que agregar un manifiesto generado manualmente al proyecto VSIX.

## <a name="file-changes-in-project-and-item-templates"></a>Cambios de archivo en las plantillas de proyecto y elemento
Mostramos los puntos de diferencia entre las versiones de Visual Studio 2015 y Visual Studio 2017 de los archivos de plantilla, para que pueda crear los nuevos archivos correctamente.

 Este es el archivo .vstemplate de proyecto predeterminado creado por Visual Studio 2015:

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ProjectTemplate1</Name>
    <Description>ProjectTemplate1</Description>
    <Icon>ProjectTemplate1.ico</Icon>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <SortOrder>1000</SortOrder>
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
    <CreateNewFolder>true</CreateNewFolder>
    <DefaultName>ProjectTemplate1</DefaultName>
    <ProvideDefaultName>true</ProvideDefaultName>
  </TemplateData>
  <TemplateContent>
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>
    </Project>
  </TemplateContent>
</VSTemplate>

```

 Aquí está el archivo .vstman (puede encontrarlo en el directorio de manifiesto del proyecto VSIX) que resultó de la reconstrucción del proyecto VSIX:

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ProjectTemplate1</Name>
        <Description>ProjectTemplate1</Description>
        <Icon>ProjectTemplate1.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>ProjectTemplate1</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 La información proporcionada por el [elemento TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) sigue siendo la misma. El ** \<elemento VSTemplateContainer>** apunta al archivo .vstemplate de la plantilla asociada.

 Este es el elemento predeterminado .vstemplate archivo creado por Visual Studio 2015:

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ItemTemplate1</Name>
    <Description>ItemTemplate1</Description>
    <Icon>ItemTemplate1.ico</Icon>
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    <DefaultName>Class.cs</DefaultName>
  </TemplateData>
  <TemplateContent>
    <References>
      <Reference>
        <Assembly>System</Assembly>
      </Reference>
    </References>
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>
  </TemplateContent>
</VSTemplate>

```

 Aquí está el archivo .vstman (puede encontrarlo en el directorio de manifiesto del proyecto VSIX) que resultó de la reconstrucción del proyecto VSIX:

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>
```

 La información proporcionada por el ** \<elemento de>TemplateData** sigue siendo la misma. El ** \<elemento VSTemplateContainer>** apunta al archivo .vstemplate para la plantilla asociada

 Para obtener más información acerca de los diferentes elementos del archivo .vstman, vea Referencia de esquema de manifiesto de plantilla de [Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Actualizaciones de extensiones instaladas con un archivo . Msi

Algunas extensiones basadas en MSI implementan plantillas en ubicaciones de plantillas comunes, como los directorios siguientes:

- **\<Directorio de instalación de Visual Studio\\>, Common7, IDE<ProjectTemplates/ItemTemplates\>**

- **\<Directorio de instalación de Visual Studio>, Common7, IDE, ExtensionName\\ \> \\<<Project/ItemTemplates\>**

Si la extensión realiza una implementación basada en MSI, debe generar el manifiesto de plantilla manualmente y asegurarse de que se incluye en la configuración de la extensión. Compare los ejemplos .vstman enumerados anteriormente y la Referencia de esquema de manifiesto de plantilla de [Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

Cree manifiestos independientes para las plantillas de proyecto y elemento, y deben apuntar al directorio de plantillas raíz como se especificó anteriormente. Cree un manifiesto por extensión y configuración regional.

## <a name="see-also"></a>Vea también

- [Solución de problemas de detección de plantillas](troubleshooting-template-discovery.md)
- [Creación de plantillas de proyectos y elementos personalizadas](creating-custom-project-and-item-templates.md)
