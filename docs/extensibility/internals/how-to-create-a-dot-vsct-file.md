---
title: 'Cómo: crear una. Archivo de Vsct | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c6456b0b866f08956862fa197719354bedf0ecf6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-vsct-file"></a>Cómo: crear una. Archivo de Vsct  
  
Hay varias maneras de crear un archivo de configuración (.vsct) basado en XML Visual Studio comando tabla.  
  
-   Puede crear un nuevo VSPackage se muestra en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plantilla de paquete.  
  
-   Puede usar el compilador de configuración de tabla de comandos basado en XML, Vsct.exe, para generar un archivo de un archivo .ctc existente.  
  
-   Puede usar Vsct.exe para generar un archivo .vsct a partir de un archivo .cto existente.  
  
-   Puede crear manualmente un nuevo archivo de vsct.  
  
 Este tema explica cómo crear manualmente un nuevo archivo de vsct.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Para crear manualmente un nuevo archivo de vsct  
  
1.  Inicie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
2.  En el **archivo** menú, elija **New**y, a continuación, haga clic en **archivo**.  
  
3.  En el **plantillas** panel, haga clic en **archivo XML** y, a continuación, haga clic en **abiertos**.  
  
4.  En el **vista** menú, haga clic en **ventana propiedades** para mostrar las propiedades del archivo XML.  
  
5.  En el **propiedades** ventana, haga clic en el botón Examinar (...) en la propiedad de esquemas.  
  
6.  En la lista de esquemas XSD, seleccione el esquema de vsct.xsd. Si no está en la lista, haga clic en **agregar** y, a continuación, busque el archivo en una unidad local. Haga clic en **Aceptar** cuando haya terminado.  
  
7.  En el archivo XML, escriba `<CommandTable` y, a continuación, presione la tecla TAB. Cerrar la etiqueta escribiendo `>`.  
  
     Esto crea un archivo .vsct básica.  
  
8.  Rellene los elementos del archivo XML que desea agregar, según la [VSCT esquema](../../extensibility/vsct-xml-schema-reference.md). Para obtener más información, consulte [creación. Archivos Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Cómo: Crear un archivo .Vsct a partir de un archivo .Ctc existente  
  
Puede crear un archivo de vsct basado en XML de un archivo de origen de comando tabla .ctc existente. Al hacerlo, puede aprovechar las ventajas del nuevo basado en XML [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] formato de compilador de tabla (VSCT) de comandos.  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Para crear un archivo .vsct a partir de un archivo .ctc existente  
  
1.  Obtenga una copia del lenguaje Perl.  
  
2.  Obtenga una copia de la secuencia de comandos Perl ConvertCTCToVSCT.pl, que normalmente se encuentra en la  *\<ruta de instalación de Visual Studio SDK >*\VisualStudioIntegration\Tools\bin carpeta.  
  
3.  Obtenga una copia del archivo .ctc de origen que desea va a convertir.  
  
4.  Coloque los archivos en el mismo directorio.  
  
5.  En el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comando ventana del símbolo del sistema, desplácese al directorio.  
  
6.  Tipo  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     donde PkgCmd.ctc es el nombre del archivo .ctc y PkgCmd.vsct es el nombre del archivo vsct que desea crear.  
  
     Esto crea un nuevo archivo de origen de tabla de comandos XML .vsct. Puede compilar el archivo usando el archivo Vsct.exe, el compilador VSCT, tal como lo haría con cualquier otro archivo .vsct.  
  
    > [!NOTE]
    >  Puede mejorar la legibilidad del archivo .vsct volviendo a asignar formato a los comentarios XML.  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Cómo: Crear un archivo .vsct a partir de un archivo .cto existente  
  
Puede crear un archivo .vsct basado en XML a partir de un archivo .cto binario existente. Si lo hace, podrá aprovechar el nuevo formato de compilador de tabla de comandos. Este proceso funciona aunque el archivo .cto esté compilado a partir de un archivo .ctc. Puede editar y compilar el archivo .vsct en otro archivo .cto.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Para crear un archivo .vsct a partir de un archivo .cto  
  
1.  Obtenga copias del archivo .cto y el archivo .ctsym correspondiente.  
  
2.  Coloque los archivos en el mismo directorio que el compilador vsct.exe.  
  
3.  En el símbolo del sistema de Visual Studio, vaya al directorio que contiene los archivos .cto y .ctsym.  
  
4.  Tipo de **vsct.exe** *ctofilename *** .cto** * vsctfilename***.vsct -S***symfilename ***ctsym**.  
  
     `ctofilename` es el nombre del archivo .cto, `vsctfilename` es el nombre del archivo vsct que desea crear, y `symfilename` es el nombre del archivo. ctsym.  
  
     Este proceso crea un nuevo archivo compilador de tabla de comandos XML .vsct. Puede editar y compilar el archivo con vsct.exe, el compilador de .vsct, tal como lo haría con cualquier otro archivo .vsct.  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Basta con agregar un archivo .vsct a un proyecto no provoca que se compile. Se debe incorporar en el proceso de compilación.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Para agregar un archivo .vsct a la compilación del proyecto  
  
1.  Abra el archivo de proyecto en el editor. Si se carga el proyecto, debe descargar primero.  
  
2.  Agregar un [elemento ItemGroup](../../msbuild/itemgroup-element-msbuild.md) que contiene un elemento VSCTCompile, tal como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     El elemento ResourceName siempre debe establecerse en `Menus.ctmenu`.  
  
3.  Si el proyecto contiene un archivo .resx, agregue un elemento de EmbeddedResource que contiene un elemento MergeWithCTO, tal como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Este marcado debería ir dentro del elemento ItemGroup que contiene recursos incrustados.  
  
4.  Abra el archivo de paquete, normalmente denominado *ProjectName*Package.cs o *ProjectName*Package.vb, en el editor.  
  
5.  Agregue un atributo ProvideMenuResource a la clase de paquete, tal como se muestra en el ejemplo siguiente.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     El primer valor del parámetro debe coincidir con el valor del atributo ResourceName definido en el archivo de proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Creación. Archivos Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Tabla de comandos de Visual Studio (. Archivos Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)