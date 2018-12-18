---
title: 'Cómo: crear una. Archivo de Vsct | Microsoft Docs'
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
ms.openlocfilehash: 612ad5668ebb1033ef07dcad1fc07030d78e1643
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921215"
---
# <a name="how-to-create-a-vsct-file"></a>Cómo: crear un archivo .vsct  
  
Hay varias maneras de crear una configuración de tabla de comandos de Visual Studio basado en XML (*.vsct*) archivo.  
  
- Puede crear un nuevo VSPackage se muestra en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plantilla de paquete.  
  
- Puede usar el compilador de configuración de tabla de comando basado en XML, *Vsct.exe*, para generar un archivo a partir de una máquina *.ctc* archivo.  
  
- Puede usar *Vsct.exe* para generar un *.vsct* archivo a partir de una máquina *.cto* archivo.  
  
- Puede crear manualmente un nuevo *.vsct* archivo.  
  
  En este artículo se explica cómo crear manualmente un nuevo *.vsct* archivo.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Para crear manualmente un nuevo archivo de vsct  
  
1. Inicie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
2. En el **archivo** menú, elija **New**y, a continuación, haga clic en **archivo**.  
  
3. En el **plantillas** panel, haga clic en **archivo XML** y, a continuación, haga clic en **abierto**.  
  
4. En el **vista** menú, haga clic en **propiedades** para mostrar las propiedades del archivo XML.  
  
5. En el **propiedades** ventana, haga clic en el **examinar** situado en la **esquemas** propiedad.  
  
6. En la lista de esquemas XSD, seleccione la *vsct.xsd* esquema. Si no está en la lista, haga clic en **agregar** y, a continuación, busque el archivo en una unidad local. Haga clic en **Aceptar** cuando haya terminado.  
  
7. En el archivo XML, escriba *< CommandTable* y, a continuación, presione **ficha**. Cerrar la etiqueta escribiendo *>*.  
  
    Esta acción crea un basic *.vsct* archivo.  
  
8. Rellenar los elementos del archivo XML que desea agregar, de acuerdo con la [referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md). Para obtener más información, consulte [crear archivos de vsct](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Cómo: crear un archivo .vsct a partir de un archivo .ctc existente  
  
Puede crear un basado en XML *.vsct* archivo desde una tabla existente del comando *.ctc* archivo de código fuente. Al hacerlo, puede aprovechar las ventajas del nuevo basado formato del compilador de la tabla de comandos (VSCT) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Para crear un archivo .vsct a partir de un archivo .ctc existente  
  
1. Obtenga una copia del lenguaje Perl.  
  
2. Obtenga una copia de la secuencia de comandos Perl *ConvertCTCToVSCT.pl*, que se encuentra normalmente en el  *\<ruta de instalación de Visual Studio SDK > \VisualStudioIntegration\Tools\bin* carpeta.  
  
3. Obtenga una copia de la *.ctc* archivo de código fuente que se va a convertir.  
  
4. Coloque los archivos en el mismo directorio.  
  
5. En el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ventana del símbolo de comandos, navegue hasta el directorio.  
  
6. Tipo  
  
   ```  
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
   ```  
  
    donde *PkgCmd.ctc* es el nombre de la *.ctc* archivo y *PkgCmd.vsct* es el nombre de la *.vsct* archivo que desea crear.  
  
    Esta acción crea un nuevo *.vsct* archivo de origen de tabla de comandos XML. Puede compilar el archivo mediante el uso de *Vsct.exe*, el compilador VSCT, como haría con cualquier otro *.vsct* archivo.  
  
   > [!NOTE]
   >  Puede mejorar la legibilidad de la *.vsct* archivo volviendo a formatear los comentarios XML.  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Cómo: crear un archivo .vsct a partir de un archivo .cto existente  
  
Puede crear un basado en XML *.vsct* archivo desde un binario existente *.cto* archivo. Si lo hace, podrá aprovechar el nuevo formato de compilador de tabla de comandos. Este asistente de proceso funciona aunque el *.cto* archivo compilado a partir de un *.ctc* archivo. Puede editar y compilar el *.vsct* en otro archivo .cto.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Para crear un archivo .vsct a partir de un archivo .cto  
  
1.  Obtenga copias de los *.cto* archivo y su correspondiente *ctsym* archivo.  
  
2.  Coloque los archivos en el mismo directorio que el *vsct.exe* compilador.  
  
3.  En el símbolo del sistema de Visual Studio, vaya al directorio que contiene el *.cto* y *ctsym* archivos.  
  
4.  Tipo  

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     donde \<ctofilename\> es el nombre de la *.cto* archivo, \<vsctfilename\> es el nombre de la *.vsct* archivo que desea volver a crear y \<symfilename\> es el nombre de la *ctsym* archivo.  
  
     Este proceso crea un nuevo *.vsct* archivo del compilador de tabla de comandos XML. Puede editar y compilar el archivo con *vsct.exe*, el compilador vsct, como haría con cualquier otro *.vsct* archivo.  
  
## <a name="compile-the-code"></a>Compilar el código  
 Simplemente agregando un *.vsct* archivo a un proyecto no hace que se va a compilar. Debe incorporarlo en el proceso de compilación.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Para agregar un archivo .vsct a la compilación del proyecto  
  
1.  Abra el archivo de proyecto en el editor. Si se carga el proyecto, primero debe descargarlo.  
  
2.  Agregar un [elemento ItemGroup](../../msbuild/itemgroup-element-msbuild.md) que contiene un `VSCTCompile` elemento, como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     El `ResourceName` elemento siempre debe establecerse en `Menus.ctmenu`.  
  
3.  Si el proyecto contiene un *.resx* , agregue un `EmbeddedResource` elemento que contiene un `MergeWithCTO` elemento, como se muestra en el ejemplo siguiente:  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Este marcado debe ir dentro el `ItemGroup` elemento que contiene recursos incrustados.  
  
4.  Abra el archivo de paquete, normalmente denominado  *\<ProjectName\>Package.cs* o  *\<ProjectName\>Package.vb*, en el editor.  
  
5.  Agregar un `ProvideMenuResource` atributo a la clase de paquete, tal como se muestra en el ejemplo siguiente.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     El primer valor del parámetro debe coincidir con el valor de la `ResourceName` atributo definido en el archivo de proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Archivos .vsct de autor](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Archivos visuales Studio comando table (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)