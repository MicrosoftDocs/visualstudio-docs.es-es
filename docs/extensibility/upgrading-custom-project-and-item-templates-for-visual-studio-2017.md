---
title: "Actualización de proyecto personalizadas y plantillas de elementos de Visual Studio &quot;15&quot; | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: af2000e6c3649b625c54ed9dc2706d64642016ad
ms.lasthandoff: 02/22/2017

---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-2017"></a>Actualización de proyecto personalizadas y plantillas de elementos de Visual Studio de 2017
A partir de 2017 de Visual Studio, Visual Studio está cambiando la forma detecta plantillas de proyecto y de elementos que se han instalado por un .vsix o un archivo .msi. Si dispone de las extensiones que utilizar plantillas de elemento o de proyecto personalizadas, debe actualizar sus extensiones. Este tema explica lo que debe hacer.  
  
 Este cambio afecta sólo de Visual Studio 2017. No afecta a las versiones anteriores de Visual Studio.  
  
 Si desea crear una plantilla de proyecto o un elemento como parte de una extensión VSIX, consulte [crear proyecto de personalizados y plantillas de elementos](../extensibility/creating-custom-project-and-item-templates.md).  
  
## <a name="template-scanning"></a>Plantilla de análisis  
 Anteriormente, **devenv /setup** o **devenv /installvstemplates** examina el disco local para buscar plantillas de proyecto y elemento. A partir del 4 de vista previa, análisis se realizará solo para la ubicación de nivel de usuario (**%USERPROFILE%\Documents\\<Visual studio=""></Visual>\>\My Exported Templates\\**) que se utiliza para plantillas generadas por la **archivo / exportar plantillas** comando.  
  
 Para otras ubicaciones (no de usuario), debe incluir un archivo manifest(.vstman) que especifica la ubicación y otras características de la plantilla. Se genera el archivo .vstman junto con el archivo .vstemplate que se utiliza para las plantillas. Si instala la extensión utilizando un .vsix, puede hacerlo al volver a compilar la extensión de Visual Studio de 2017. Pero si utiliza un archivo .msi, debe realizar los cambios manualmente. Para obtener una lista de lo que necesita hacer para que estos cambios, consulte **actualizaciones de extensiones se instalan con una. MSI** más adelante en este tema.  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Cómo actualizar una extensión VSIX con plantillas de elemento o de proyecto  
 Este procedimiento explica cómo hacer que Visual Studio de 2017
1.  Abra la solución en Visual Studio de 2017. Deberá actualizar el código. Haga clic en **Aceptar**.  
  
2.  Una vez completada la actualización, debe cambiar la versión de destino de la instalación. En el proyecto VSIX, abra el archivo source.extension.vsixmanifest y seleccione la **destinos de instalación** ficha. Si el **intervalo de versiones** campo es **[14.0]**, haga clic en **editar** y cámbiela para que incluya 2017 de Visual Studio. Por ejemplo, puede establecer en **[14.0,15.0]** para instalar la extensión de Visual Studio 2015 o 2017 de Visual Studio, o de **[15.0]** instalar que acaba de Visual Studio 2017.  
  
3.  Vuelva a compilar el código.  
  
4.  Cierre Visual Studio.  
  
5.  Instale la extensión VSIX.  
  
6.  Puede probar la actualización haciendo lo siguiente:  
  
    1.  El archivo de análisis de cambio se activa por la clave del registro siguiente:  
  
         **reg agregar hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  Después de haber agregado la clave, ejecute **devenv /installvstemplates**.  
  
    3.  Vuelva a abrir Visual Studio. Debe buscar la plantilla en la ubicación esperada.  
  
    > [!NOTE]
    >  Las plantillas de proyecto de extensibilidad de Visual Studio no están disponibles cuando la clave del registro está presente. Debe eliminar la clave del registro (y vuelva a ejecutar **devenv /installvstemplates**) para usarlos.  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Otras recomendaciones para la implementación de proyecto y plantillas de elementos  
  
-   Evite utilizar archivos de plantilla comprimidos. Comprimir archivos deben estar sin comprimir con el fin de recuperar recursos y contenido de plantilla, así será costosa usar. En su lugar, debería implementar plantillas de proyecto y elementos como archivos individuales en su propio directorio para acelerar la inicialización de la plantilla. Para las extensiones VSIX, las tareas de compilación SDK descomprimirá automáticamente cualquier plantilla comprimido al crear el archivo VSIX.  
  
-   Evite el uso de las entradas de identificador de paquete o un recurso de nombre de la plantilla, descripción, icono o vista previa con el fin de evitar las cargas de ensamblado de recursos innecesarios durante la detección de la plantilla. En su lugar, puede utilizar manifiestos localizados para crear una entrada de plantilla para cada configuración regional, que utiliza nombres localizados o propiedades.  
  
-   Si incluye plantillas de elementos de archivo, la generación de manifiestos podría no proporcionar los resultados esperados. En ese caso, tendrá que agregar un manifiesto generado manualmente al proyecto VSIX.  
  
## <a name="file-changes-in-project-and-item-templates"></a>Cambios en el archivo de proyecto y plantillas de elementos  
 Le mostraremos los puntos de la diferencia entre la versión de Visual Studio 2015 y la versión de Visual Studio "15" de los archivos de plantilla, para que pueda crear los nuevos archivos correctamente.  
  
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
  
 Este es el archivo de .vstman (lo puede encontrar en el directorio de manifiesto del proyecto VSIX) que se obtienen de la regeneración del proyecto VSIX:  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
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
  
 La información proporcionada por el [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) elemento sigue siendo la misma. El ** \<VSTemplateContainer >** elemento apunta al archivo .vstemplate de la plantilla asociada.  
  
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
  
 Este es el archivo de .vstman (lo puede encontrar en el directorio de manifiesto del proyecto VSIX) que se obtienen de la regeneración del proyecto VSIX:  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
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
  
 La información proporcionada por el ** \<TemplateData >** elemento sigue siendo la misma. El ** \<VSTemplateContainer >** elemento apunta al archivo .vstemplate de la plantilla asociada  
  
 Para obtener más información acerca de los distintos elementos del archivo .vstman, consulte [Visual Studio Template manifiesto Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Las actualizaciones para las extensiones se instalan con una. MSI  
 Algunas extensiones basadas en MSI implementación plantillas en ubicaciones de plantillas comunes como la siguiente:  
  
-   **\<Directorio de instalación de Visual Studio > \Common7\IDE\\<ProjectTemplates temtemplates="">**</ProjectTemplates>  
  
-   **\<Directorio de instalación de Visual Studio > \Common7\IDE\Extensions\\<>\>\\<Project temtemplates="">**</Project>  
  
 Si la extensión realiza una implementación basada en MSI, debe generar el manifiesto de la plantilla manualmente y asegurarse de que se incluye en la instalación de la extensión. Debe comparar los ejemplos de .vstman enumerados anteriormente y la [Visual Studio Template manifiesto Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md). Para ver lo que necesita incluir  
  
 Debe crear los manifiestos separados para las plantillas de proyecto y elemento y apunten a plantilla directorio raíz especificado anteriormente. Debe crear un manifiesto por la extensión y la configuración regional.  
  
## <a name="troubleshooting-template-installation"></a>Solución de problemas de instalación de la plantilla  
 Si experimenta problemas al implementar las plantillas de proyecto o elemento, puede habilitar el registro de diagnóstico.  
  
1.  Ejecute el comando siguiente para establecer la clave del registro para habilitar el registro:  
  
     **reg agregar HKCU\software\microsoft\visualstudio\15.0_Config\VSTemplate /v EnableTemplateDiscoveryLog /t REG_DWORD /d 1**  
  
2.  Inicie Visual Studio y los cuadros de diálogo nuevo proyecto y el nuevo elemento para inicializar ambos árboles de plantilla de inicio. El registro de la plantilla aparece ahora en **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0\VsTemplateDiagnosticsList.csv**. Cada inicialización de árbol de plantilla anexa entradas en este registro.  
  
 El archivo de registro contiene las columnas siguientes:  
  
-   **FullPathToTemplate**, que tiene los siguientes valores:  
  
    -   1 para la implementación basada en manifiestos  
  
    -   0 para la implementación basada en disco  
  
-   **TemplateFileName**  
  
-   Otras propiedades de plantilla
