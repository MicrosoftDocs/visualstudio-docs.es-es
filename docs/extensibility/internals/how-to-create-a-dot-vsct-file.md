---
title: "C&#243;mo: crear una. Archivo de Vsct | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Archivos VSCT, crear"
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: crear una. Archivo de Vsct
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Hay varias maneras de crear un archivo de configuración \(.vsct\) basado en XML y Visual Studio comando de tablas.  
  
-   Puede crear un VSPackage nuevo en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plantilla de paquete.  
  
-   Puede utilizar el compilador de configuración de tabla de comandos basado en XML, Vsct.exe, para generar un archivo de un archivo de .ctc existente.  
  
-   Puede usar Vsct.exe para generar un archivo de vsct de un archivo de .cto existente.  
  
-   Puede crear manualmente un nuevo archivo de vsct.  
  
 Este tema explica cómo crear manualmente un nuevo archivo de vsct.  
  
### Para crear manualmente un nuevo archivo de vsct  
  
1.  Inicie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
2.  En el **archivo** menú, seleccione **nuevo**, y, a continuación, haga clic en **archivo**.  
  
3.  En el **plantillas** panel, haga clic en **archivo XML** y, a continuación, haga clic en **abiertos**.  
  
4.  En el **vista** menú, haga clic en **ventana propiedades** para mostrar las propiedades del archivo XML.  
  
5.  En el **propiedades** ventana, haga clic en el botón Examinar \(...\) botón de la propiedad de esquemas.  
  
6.  En la lista de esquemas XSD, seleccione el esquema de vsct.xsd. Si no está en la lista, haga clic en **Agregar** y, a continuación, busque el archivo en una unidad local. Haga clic en **Aceptar** cuando haya terminado.  
  
7.  En el archivo XML, escriba `<CommandTable` y, a continuación, presione la tecla TAB. Cerrar la etiqueta escribiendo `>`.  
  
     Esto crea un archivo de vsct básica.  
  
8.  Rellenar los elementos del archivo XML que desea agregar, de acuerdo con la [VSCT esquema](../../extensibility/vsct-xml-schema-reference.md). Para obtener más información, vea [Creación. Archivos de Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## Compilar el código  
 Simplemente agrega un archivo de vsct a un proyecto no provoca que se compile. Se debe incluir en el proceso de compilación.  
  
### Para agregar un archivo de vsct para la compilación del proyecto  
  
1.  Abra el archivo de proyecto en el editor. Si se carga el proyecto, debe descargar primero.  
  
2.  Agregar un [elemento ItemGroup](../../msbuild/itemgroup-element-msbuild.md) que contiene un elemento VSCTCompile, como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     El elemento ResourceName siempre debe establecerse en `Menus.ctmenu`.  
  
3.  Si el proyecto contiene un archivo .resx, agregue un elemento de EmbeddedResource que contiene un elemento MergeWithCTO, como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Este marcado debería ir dentro del elemento ItemGroup que contiene recursos incrustados.  
  
4.  Abra el archivo de paquete, normalmente denominado *ProjectName*Package.cs o *ProjectName*Package.vb en el editor.  
  
5.  Agregue un atributo ProvideMenuResource a la clase de paquete, tal como se muestra en el ejemplo siguiente.  
  
    ```c#  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     Valor del primer parámetro debe coincidir con el valor del atributo ResourceName definido en el archivo de proyecto.  
  
## Vea también  
 [Creación. Archivos de Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Cómo: Crear un archivo .Vsct a partir de un archivo .Ctc existente](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Cómo: Crear un archivo .vsct a partir de un archivo .cto existente](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)