---
title: 'Cómo: crear un. Archivo Vsct | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a2483c000bb7c9446ac51bb94ef4006a7b2ac89f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158344"
---
# <a name="how-to-create-a-vsct-file"></a>Creación de un archivo .Vsct
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hay varias maneras de crear un archivo de configuración de tabla de comandos de Visual Studio (. Vsct) basado en XML.  
  
- Puede crear un nuevo VSPackage en la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] plantilla de paquete.  
  
- Puede usar el compilador de configuración de tabla de comandos basado en XML, Vsct.exe, para generar un archivo a partir de un archivo. CTC existente.  
  
- Puede usar Vsct.exe para generar un archivo. Vsct a partir de un archivo. CTO existente.  
  
- Puede crear un nuevo archivo. Vsct de forma manual.  
  
  En este tema se explica cómo crear manualmente un nuevo archivo. Vsct.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Para crear manualmente un nuevo archivo. Vsct  
  
1. Inicie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
2. En el menú **Archivo** , elija **Nuevo**y haga clic en **Archivo**.  
  
3. En el panel **plantillas** , haga clic en **archivo XML** y, a continuación, haga clic en **abrir**.  
  
4. En el menú **Ver** , haga clic en **ventana Propiedades** para mostrar las propiedades del archivo XML.  
  
5. En la ventana **propiedades** , haga clic en el botón Examinar (...) de la propiedad esquemas.  
  
6. En la lista de esquemas XSD, seleccione el esquema Vsct. xsd. Si no está en la lista, haga clic en **Agregar** y, a continuación, busque el archivo en una unidad local. Cuando haya terminado, haga clic en **Aceptar** .  
  
7. En el archivo XML, escriba `<CommandTable` y, a continuación, presione TAB. Cierre la etiqueta escribiendo `>` .  
  
     Esto crea un archivo. Vsct básico.  
  
8. Rellene los elementos del archivo XML que desea agregar, de acuerdo con el [esquema VSCT](../../extensibility/vsct-xml-schema-reference.md). Para obtener más información, consulte [creación. Archivos Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Simplemente agregar un archivo. Vsct a un proyecto no hace que se compile. Debe incorporarlo en el proceso de compilación.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Para agregar un archivo. Vsct a la compilación del proyecto  
  
1. Abra el archivo de proyecto en el editor. Si el proyecto está cargado, debe descargarlo primero.  
  
2. Agregue un [elemento ItemGroup](../../msbuild/itemgroup-element-msbuild.md) que contenga un elemento VSCTCompile, tal y como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     El elemento ResourceName siempre debe establecerse en `Menus.ctmenu` .  
  
3. Si el proyecto contiene un archivo. resx, agregue un elemento EmbeddedResource que contenga un elemento MergeWithCTO, como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Este marcado debe ir dentro del elemento ItemGroup que contiene recursos incrustados.  
  
4. Abra el archivo de paquete, normalmente denominado *ProjectName*package.cs o *projectname*package. VB, en el editor.  
  
5. Agregue un atributo ProvideMenuResource a la clase package, tal como se muestra en el ejemplo siguiente.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     El primer valor de parámetro debe coincidir con el valor del atributo ResourceName que definió en el archivo de proyecto.  
  
## <a name="see-also"></a>Consulte también  
 [Creación. Archivos Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Tabla de comandos de Visual Studio (. Archivos de Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Cómo: crear un. Archivo Vsct de un existente. Archivo CTC](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Cómo: crear un. Archivo Vsct de un existente. Archivo CTO](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)
