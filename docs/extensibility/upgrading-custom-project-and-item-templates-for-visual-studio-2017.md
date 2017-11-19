---
title: Actualizar plantillas para proyectos y plantillas de elementos de Visual Studio de 2017 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 76437dff5aa59e4864216318e64a07245c15c68d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-2017"></a>Actualizar plantillas para proyectos y plantillas de elementos de Visual Studio de 2017
A partir de 2017 de Visual Studio, Visual Studio está cambiando la forma detecta plantillas de proyecto y de elementos que se han instalado por un .vsix o un archivo .msi. Si dispone de extensiones que usan plantillas para proyectos o plantillas de elementos, debe actualizar sus extensiones. Este tema explica lo que debe hacer.  
  
 Este cambio afecta solo Visual Studio 2017. No afecta a las versiones anteriores de Visual Studio.  
  
 Si desea crear una plantilla de proyecto o un elemento como parte de una extensión VSIX, vea [crear un proyecto y plantillas de elementos](../extensibility/creating-custom-project-and-item-templates.md).  
  
## <a name="template-scanning"></a>Plantilla de análisis  
 Anteriormente, **devenv /setup** o **devenv /installvstemplates** examina el disco local para buscar plantillas de proyecto y elemento. A partir de Preview 4, análisis se realizará solo para la ubicación de nivel de usuario (**%USERPROFILE%\Documents\\< versión de Visual Studio\>\My Exported Templates\\**) que se utiliza para plantillas generadas por la **archivo / exportar plantillas** comando.  
  
 Para otras ubicaciones (no es de usuario), debe incluir un archivo manifest(.vstman) que especifica la ubicación y otras características de la plantilla. Se genera el archivo .vstman junto con el archivo .vstemplate utilizado para las plantillas. Si instala la extensión utilizando un .vsix, puede hacerlo volviendo a compilar la extensión en Visual Studio de 2017. Pero si utiliza un archivo .msi, debe realizar los cambios manualmente. Para obtener una lista de lo que necesita hacer para que estos cambios, consulte **actualizaciones para las extensiones se instalan con una. MSI** más adelante en este tema.  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Cómo actualizar una extensión VSIX con plantillas de elemento o de proyecto  
 Este procedimiento explica cómo hacer que Visual Studio de 2017
1.  Abra la solución en Visual Studio de 2017. Le pedirá que actualice el código. Haga clic en **Aceptar**.  
  
2.  Una vez completada la actualización, debe cambiar la versión de destino de la instalación. En el proyecto VSIX, abra el archivo source.extension.vsixmanifest y seleccione el **destinos de instalación** ficha. Si el **intervalo de versiones** campo es **[14.0]**, haga clic en **editar** y cámbiela para que incluya 2017 de Visual Studio. Por ejemplo, puede establecerlo en **[14.0,15.0]** para instalar la extensión en Visual Studio 2015 o Visual Studio de 2017 o a **[15.0]** para instalar en solo Visual Studio 2017.  
  
3.  Vuelva a compilar el código.  
  
4.  Cierre Visual Studio.  
  
5.  Instale la extensión VSIX.  
  
6.  Puede probar la actualización haciendo lo siguiente:  
  
    1.  El archivo de examen de cambio se activa mediante la clave del registro siguiente:  
  
         **reg agregar hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  Después de haber agregado la clave, ejecute **devenv /installvstemplates**.  
  
    3.  Vuelva a abrir Visual Studio. Debería encontrar la plantilla en la ubicación esperada.  
  
    > [!NOTE]
    >  Las plantillas de proyecto de extensibilidad de Visual Studio no están disponibles cuando la clave del registro está presente. Debe eliminar la clave del registro (y vuelva a ejecutar **devenv /installvstemplates**) para usarlos.  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Otras recomendaciones para la implementación de proyecto y plantillas de elementos  
  
-   Evite el uso de archivos de plantilla comprimido. Comprimir archivos deben estar sin comprimir para recuperar los recursos y el contenido de plantilla, por lo que estará costosa usar. En su lugar, debería implementar plantillas de proyecto y de elementos como archivos individuales en su propio directorio para acelerar la inicialización de la plantilla. Para las extensiones VSIX, las tareas de compilación SDK descompresión automáticamente cualquier plantilla comprimido al crear el archivo VSIX.  
  
-   Evite el uso de las entradas de Id. de paquete o un recurso para el nombre de la plantilla, la descripción, el icono o la vista previa con el fin de evitar las cargas de ensamblado de recursos innecesarios durante la detección de la plantilla. En su lugar, puede utilizar manifiestos localizados para crear una entrada de plantilla para cada configuración regional, que utiliza nombres localizados o propiedades.  
  
-   Si va a incluir plantillas como elementos de archivo, generación de manifiestos podría no proporcionarle los resultados esperados. En ese caso, tendrá que agregar un manifiesto generado manualmente al proyecto VSIX.  
  
## <a name="file-changes-in-project-and-item-templates"></a>Cambios del archivo de proyecto y plantillas de elementos  
Se muestran los puntos de diferencia entre las versiones de Visual Studio de 2017 de los archivos de plantilla y Visual Studio 2015 para que pueda crear los nuevos archivos correctamente.  
  
 Este es el archivo de .vstemplate de proyecto predeterminado creado por Visual Studio 2015:  
  
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
  
 Éste es el archivo de .vstman (que encontrará en el directorio de manifiesto del proyecto VSIX) que dan como resultado de la regeneración del proyecto VSIX:  
  
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
  
 La información proporcionada por el [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) elemento sigue siendo el mismo. El  **\<VSTemplateContainer >** elemento apunta al archivo .vstemplate de la plantilla asociada.  
  
 Este es el archivo de .vstemplate de elemento predeterminado creado por Visual Studio 2015:  
  
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
  
 Éste es el archivo de .vstman (que encontrará en el directorio de manifiesto del proyecto VSIX) que dan como resultado de la regeneración del proyecto VSIX:  
  
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
  
 La información proporcionada por el  **\<TemplateData >** elemento sigue siendo el mismo. El  **\<VSTemplateContainer >** elemento apunta al archivo .vstemplate de la plantilla de asociados  
  
 Para obtener más información acerca de los diferentes elementos del archivo .vstman, consulte [referencia de esquema del manifiesto de Visual Studio plantilla](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Las actualizaciones para las extensiones se instalan con una. MSI  
 Algunas extensiones basadas en MSI implementación plantillas en ubicaciones de plantillas comunes como el siguiente:  
  
-   **\<Directorio de instalación de Visual Studio > \Common7\IDE\\< ProjectTemplates/elementos >**  
  
-   **\<Directorio de instalación de Visual Studio > \Common7\IDE\Extensions\\< NombreExtensión\>\\< proyecto/elementos >**  
  
 Si su extensión llevará a cabo una implementación basada en MSI, debe generar el manifiesto de plantilla manualmente y asegúrese de que esté incluido en la instalación de la extensión. Debe comparar los ejemplos de .vstman enumerados anteriormente y el [referencia de esquema del manifiesto de Visual Studio plantilla](../extensibility/visual-studio-template-manifest-schema-reference.md). Para ver lo que necesita incluir  
  
 Se deben crear manifiestos separados para las plantillas de proyecto y elemento, y deben apuntar a plantilla directorio raíz especificado anterior. Debe crear un manifiesto por la extensión y la configuración regional.  
  
## <a name="troubleshooting-template-installation"></a>Solución de problemas de instalación de la plantilla  
 Si experimenta problemas de implementación de las plantillas de proyecto o un elemento, puede habilitar el registro de diagnóstico.  
  
1.  Cree un archivo pkgdef en la carpeta Common7\IDE\CommonExtensions para la instalación (por ejemplo, C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) con el siguiente contenido:  
  
     ```
     [$RootKey$\VsTemplate]
     "EnableTemplateDiscoveryLog"=dword:00000001
     ```

2. Abra un "símbolo" para la instalación mediante una búsqueda en búsqueda de Windows y ejecute `devenv /updateConfiguration`.

3.  Inicie Visual Studio e inicie los cuadros de diálogo nuevo proyecto y el nuevo elemento para inicializar dos árboles de plantilla. El registro de plantilla aparece ahora en **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid se corresponde con el identificador de instalación de la instancia de Visual Studio). La inicialización de árbol de cada plantilla anexa entradas para este registro.  
  
 El archivo de registro contiene las columnas siguientes:  
  
-   **FullPathToTemplate**, que tiene los siguientes valores:  
  
    -   1 para la implementación basada en manifiestos  
  
    -   0 para la implementación basada en disco  
  
-   **TemplateFileName**  
  
-   Otras propiedades de plantilla

Nota: Para deshabilitar el registro, quite el archivo pkgdef o cambie el valor de `EnableTemplateDiscoveryLog` a `dword:00000000` y ejecute `devenv /updateConfiguration` nuevo.