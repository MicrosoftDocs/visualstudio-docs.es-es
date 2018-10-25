---
title: Actualización de plantillas de elementos y proyectos personalizadas para Visual Studio "15" | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9137510f8d6949271a255b14b293f59366048f77
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923451"
---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-15"></a>Actualización de plantillas de elementos y proyectos personalizadas para Visual Studio "15"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A partir de Visual Studio "15" Preview 4, Visual Studio está cambiando la forma detecta plantillas de proyecto y elemento que se han instalado por un .vsix o. msi. Si dispone de extensiones que usan las plantillas de elemento o de proyecto personalizado, deberá actualizar sus extensiones. En este tema se explica lo que debe hacer.  
  
 Este cambio afecta solo a Visual Studio "15". No afecta a las versiones anteriores de Visual Studio.  
  
 Si desea crear una plantilla de proyecto o elemento como parte de una extensión VSIX, vea [crear un proyecto y plantillas de elementos](../extensibility/creating-custom-project-and-item-templates.md).  
  
## <a name="template-scanning"></a>Plantilla de análisis  
 Anteriormente, **devenv /setup** o **devenv /installvstemplates** examina el disco local para buscar plantillas de proyecto y elemento. A partir de Preview 4, examen se realizará solo para la ubicación de nivel de usuario (**%USERPROFILE%\Documents\\< versión de Visual Studio\>\My Exported Templates\\**) que se usa para plantillas generadas por la **archivo / exportar plantillas** comando.  
  
 Para otras ubicaciones (no de usuario), debe incluir un archivo manifest(.vstman) que especifica la ubicación y otras características de la plantilla. Se genera el archivo vstman junto con el archivo .vstemplate que se usa para las plantillas. Si instala la extensión con un VSIX, puede hacerlo al volver a compilar la extensión en Visual Studio "15" Preview 2. Pero si usa un archivo .msi, deberá realizar los cambios manualmente. Para obtener una lista de lo que necesita hacer para que estos cambios, consulte **actualizaciones para las extensiones se instalan con una. MSI** más adelante en este tema.  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Cómo actualizar una extensión VSIX con plantillas de elemento o proyecto  
 Este procedimiento explica cómo hacer la actualización de Visual Studio "15" Preview 2 la extensión VSIX existente.  
  
1.  Abra la solución en Visual Studio "15" Preview 2. Se le pedirá que actualice el código. Haga clic en **Aceptar**.  
  
2.  Una vez finalizada la actualización, deberá cambiar la versión de destino de la instalación. En el proyecto VSIX, abra el archivo source.extension.vsixmanifest y seleccione el **destinos de instalación** ficha. Si el **intervalo de versiones** campo es **[14.0]**, haga clic en **editar** y cámbielo para incluir Visual Studio "15". Por ejemplo, puede establecer en **[14.0,15.0]** para instalar la extensión para Visual Studio 2015 o Visual Studio "15", o para **[15.0]** para instalarlo en Visual Studio "15" simplemente.  
  
3.  Vuelva a compilar el código.  
  
4.  Cierre Visual Studio.  
  
5.  Instale la extensión VSIX.  
  
6.  Puede probar la actualización haciendo lo siguiente:  
  
    1.  El archivo de examen de cambio se activa por la clave del registro siguiente:  
  
         **reg agregar hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  Después de haber agregado la clave, ejecute **devenv /installvstemplates**.  
  
    3.  Vuelva a abrir Visual Studio. Debería encontrar una plantilla en la ubicación esperada.  
  
    > [!NOTE]
    >  Las plantillas de proyecto de extensibilidad de Visual Studio no están disponibles cuando la clave del registro está presente. Debe eliminar la clave del registro (y vuelva a ejecutar **devenv /installvstemplates**) para usarlos.  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Otras recomendaciones para la implementación de plantillas de proyecto y elemento  
  
-   Evite el uso de archivos de plantilla comprimido. Comprimir archivos deben estar sin comprimir con el fin de recuperar los recursos y el contenido de plantilla, por lo que estarán más costosas serán a usar. En su lugar, debe implementar las plantillas de proyectos y elementos como archivos individuales en su propio directorio para acelerar la inicialización de la plantilla. Para las extensiones VSIX, las tareas de compilación SDK lo descomprimirá automáticamente cualquier plantilla comprimido al crear el archivo VSIX.  
  
-   Evite el uso de las entradas de Id. de recurso del paquete para el nombre de la plantilla, descripción, icono o versión preliminar con el fin de evitar las cargas de ensamblado de recursos innecesarios durante la detección de plantillas. En su lugar, puede usar manifiestos localizados para crear una entrada de plantilla para cada configuración regional, que utiliza nombres localizados o propiedades.  
  
-   Si va a incluir plantillas de elementos de archivo, la generación de manifiestos no es posible que produzca los resultados esperados. En ese caso, tendrá que agregar un manifiesto generado manualmente al proyecto de VSIX.  
  
## <a name="file-changes-in-project-and-item-templates"></a>Cambios del archivo de proyecto y plantillas de elementos  
 Le mostraremos los puntos de diferencia entre la versión de Visual Studio 2015 y la versión de Visual Studio "15" de los archivos de plantilla, para que pueda crear los nuevos archivos correctamente.  
  
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
  
 Este es el archivo de vstman (puede encontrarla en el directorio de manifiesto del proyecto VSIX) que dan como resultado de la regeneración del proyecto VSIX:  
  
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
  
 La información proporcionada por el [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) elemento sigue siendo el mismo. El  **\<VSTemplateContainer >** elemento apunta al archivo .vstemplate de la plantilla asociada.  
  
 Este es el archivo .vstemplate de elementos predeterminado creado por Visual Studio 2015:  
  
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
  
 Este es el archivo de vstman (puede encontrarla en el directorio de manifiesto del proyecto VSIX) que dan como resultado de la regeneración del proyecto VSIX:  
  
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
  
 La información proporcionada por el  **\<TemplateData >** elemento sigue siendo el mismo. El  **\<VSTemplateContainer >** elemento apunta al archivo .vstemplate de la plantilla asociada  
  
 Para obtener más información acerca de los diferentes elementos del archivo vstman, consulte [referencia de esquema de manifiesto de Visual Studio plantilla](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Las actualizaciones para las extensiones se instalan con una. MSI  
 Algunas extensiones basadas en MSI implementación plantillas en las ubicaciones de plantillas comunes como el siguiente:  
  
- **\<Directorio de instalación de Visual Studio > \Common7\IDE\\< ProjectTemplates/ItemTemplates >**  
  
- **\<Directorio de instalación de Visual Studio > \common7\ide\extensions\\\< ExtensionName\>\\< proyecto/ItemTemplates >**  
  
  Si la extensión lleva a cabo una implementación basada en MSI, deberá generar el manifiesto de plantilla manualmente y asegúrese de que se incluye en la instalación de la extensión. Debería comparar los ejemplos de vstman enumerados anteriormente y el [referencia de esquema de manifiesto de Visual Studio plantilla](../extensibility/visual-studio-template-manifest-schema-reference.md). Para ver lo que necesita incluir  
  
  Se deben crear manifiestos separados para las plantillas de proyecto y elemento, y deben apuntar a la plantilla directorio raíz especificado anteriormente. Debe crear un manifiesto por la extensión y la configuración regional.  
  
## <a name="troubleshooting-template-installation"></a>Solución de problemas de instalación de la plantilla  
 Si experimenta problemas al implementar las plantillas de proyecto o elemento, puede habilitar el registro de diagnóstico.  
  
1. Ejecute el siguiente comando para establecer la clave del registro para habilitar el registro:  
  
    **reg agregar HKCU\software\microsoft\visualstudio\15.0_Config\VSTemplate /v EnableTemplateDiscoveryLog /t REG_DWORD /d 1**  
  
2. Iniciar Visual Studio y los cuadros de diálogo nuevo proyecto y el nuevo elemento para inicializar ambos árboles de plantilla. El registro de plantilla aparece ahora en **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0\VsTemplateDiagnosticsList.csv**. La inicialización de cada árbol de la plantilla anexa entradas en este registro.  
  
   El archivo de registro contiene las columnas siguientes:  
  
-   **FullPathToTemplate**, que tiene los siguientes valores:  
  
    -   1 para la implementación basada en manifiesto  
  
    -   0 para la implementación basada en disco  
  
-   **TemplateFileName**  
  
-   Otras propiedades de plantilla

