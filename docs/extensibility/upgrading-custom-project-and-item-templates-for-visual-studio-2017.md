---
title: Actualización de plantillas de proyecto y de elemento personalizadas para Visual Studio 2017
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698860"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Actualización de Plantillas de proyecto y elemento para Visual Studio personalizado 2017

A partir de Visual Studio 2017, Visual Studio detecta plantillas de proyecto y elemento que se han instalado mediante un archivo. vsix o un archivo. msi de una forma diferente a las versiones anteriores de Visual Studio. Si posee extensiones que usan plantillas de proyecto o de elemento personalizadas, debe actualizar las extensiones. En este artículo se explica lo que debe hacer.

Este cambio solo afecta a Visual Studio 2017. No afecta a las versiones anteriores de Visual Studio.

Si desea crear una plantilla de proyecto o elemento como parte de una extensión VSIX, vea [crear plantillas de proyecto y de elemento personalizadas](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Examen de plantillas

En versiones anteriores de Visual Studio, **devenv/Setup** o **devenv/installvstemplates** examinaban el disco local para buscar plantillas de proyecto y de elemento. A partir de Visual Studio 2017, el examen solo se realiza para la ubicación de nivel de usuario. La ubicación predeterminada del nivel de usuario es **%USERPROFILE%\Documents \\<Visual Studio \> versión \\ \Templates**. Esta ubicación se usa para las plantillas generadas **Project**por el  >  comando**exportar plantillas.** .. de proyecto si la opción **importar automáticamente la plantilla en Visual Studio** está seleccionada en el asistente.

En el caso de otras ubicaciones (no de usuario), debe incluir un archivo de manifiesto (. vstman) que especifique la ubicación y otras características de la plantilla. El archivo. vstman se genera junto con el archivo. vstemplate usado para las plantillas. Si instala la extensión con un. vsix, puede hacerlo volviendo a compilar la extensión en Visual Studio 2017. Pero si usa un archivo. msi, debe realizar los cambios manualmente. Para obtener una lista de lo que debe hacer para realizar estos cambios, consulte  **actualizaciones de las extensiones instaladas con un. MSI** más adelante en esta página.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Cómo actualizar una extensión VSIX con plantillas de proyecto o elemento

1. Abra la solución en Visual Studio 2017. Se le pedirá que actualice el código. Haga clic en **OK**.

2. Una vez finalizada la actualización, es posible que deba cambiar la versión del destino de instalación. En el Proyecto VSIX, abra el archivo source. Extension. vsixmanifest y seleccione la pestaña **destinos de instalación** . Si el campo **intervalo de versión** es **[14,0]**, haga clic en **Editar** y cámbielo para incluir Visual Studio 2017. Por ejemplo, puede establecerlo en **[14.0, 15.0]** para instalar la extensión en visual Studio 2015 o visual Studio 2017 o en **[15,0]** para instalarlo en solo Visual Studio 2017.

3. Vuelva a compilar el código.

4. Cierre Visual Studio.

5. Instale el VSIX.

6. Puede probar la actualización de la siguiente manera:

    1. La siguiente clave del registro activa el cambio de análisis de archivos:

         **REG Add hklm\software\microsoft\visualstudio\15.0\VSTemplate/v DisableTemplateScanning/t REG_DWORD/d 1/reg: 32**

    2. Después de agregar la clave, ejecute **devenv/installvstemplates**.

    3. Vuelva a abrir Visual Studio. La plantilla debe encontrarse en la ubicación esperada.

    > [!NOTE]
    > Las plantillas de proyecto de extensibilidad de Visual Studio no están disponibles cuando la clave del registro está presente. Debe eliminar la clave del registro (y volver a ejecutar **devenv/installvstemplates**) para usarlas.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Otras recomendaciones para la implementación de plantillas de proyecto y de elemento

- Evite el uso de archivos de plantilla comprimidos. Los archivos de plantilla comprimidos se deben descomprimir para recuperar recursos y contenido, de modo que se más costosas serán a usar. En su lugar, debe implementar plantillas de proyecto y de elemento como archivos individuales en su propio directorio para acelerar la inicialización de la plantilla. Para las extensiones VSIX, las tareas de compilación de SDK descomprimen automáticamente cualquier plantilla comprimida mientras se crea el archivo VSIX.

- Evite el uso de entradas de identificador de paquete/recurso para el nombre, la descripción, el icono o la vista previa de la plantilla con el fin de evitar cargas innecesarias de ensamblado de recursos durante la detección de plantillas. En su lugar, puede usar manifiestos localizados para crear una entrada de plantilla para cada configuración regional, que usa nombres o propiedades localizados.

- Si va a incluir plantillas como elementos de archivo, es posible que la generación de manifiestos no proporcione los resultados esperados. En ese caso, tendrá que agregar un manifiesto generado manualmente al Proyecto VSIX.

## <a name="file-changes-in-project-and-item-templates"></a>Cambios de archivos en plantillas de proyecto y elemento
Se muestran los puntos de diferencia entre las versiones de Visual Studio 2015 y Visual Studio 2017 de los archivos de plantilla, de modo que puede crear los nuevos archivos correctamente.

 Este es el archivo Project. vstemplate predeterminado creado por Visual Studio 2015:

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

 Este es el archivo. vstman (puede encontrarlo en el directorio del manifiesto del Proyecto VSIX) que resultó de la regeneración del Proyecto VSIX:

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

 La información proporcionada por el elemento [TemplateData (](../extensibility/templatedata-element-visual-studio-templates.md) sigue siendo la misma. El **\<VSTemplateContainer>** elemento apunta al archivo. vstemplate para la plantilla asociada.

 Este es el archivo. vstemplate predeterminado creado por Visual Studio 2015:

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

 Este es el archivo. vstman (puede encontrarlo en el directorio del manifiesto del Proyecto VSIX) que resultó de la regeneración del Proyecto VSIX:

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

 La información proporcionada por el **\<TemplateData>** elemento sigue siendo la misma. El **\<VSTemplateContainer>** elemento apunta al archivo. vstemplate para la plantilla asociada.

 Para obtener más información sobre los distintos elementos del archivo. vstman, vea [referencia de esquema de manifiesto de plantilla de Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Actualizaciones para las extensiones instaladas con. MS

Algunas extensiones basadas en MSI implementan plantillas en ubicaciones de plantillas comunes, como los directorios siguientes:

- **\<Visual Studio installation directory>\Common7\IDE \\<ProjectTemplates/ItemTemplates\>**

- **\<Visual Studio installation directory>\Common7\IDE\Extensions \\<ExtensionName \> \\<proyecto/ItemTemplates\>**

Si la extensión realiza una implementación basada en MSI, debe generar manualmente el manifiesto de plantilla y asegurarse de que se incluye en la configuración de la extensión. Compare los ejemplos de. vstman enumerados anteriormente y la [referencia de esquema de manifiesto de plantilla de Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

Cree manifiestos independientes para las plantillas de proyecto y de elemento, y deben apuntar al directorio de plantillas raíz tal y como se especificó anteriormente. Cree un manifiesto por extensión y configuración regional.

## <a name="see-also"></a>Consulte también

- [Solución de problemas de detección de plantillas](troubleshooting-template-discovery.md)
- [Crear plantillas de proyecto y de elemento personalizadas](creating-custom-project-and-item-templates.md)
