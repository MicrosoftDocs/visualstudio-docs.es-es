---
title: 'Cómo: Crear un archivo . Archivo vsct ??????????? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5a5f53ec87c9447af232e9d0528108ddbaea01a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708109"
---
# <a name="how-to-create-a-vsct-file"></a>Cómo: Crear un archivo .vsct

Hay varias maneras de crear un archivo de configuración de tabla de comandos de Visual Studio basado en XML (*.vsct*).

- Puede crear un nuevo VSPackage en la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plantilla de paquete.

- Puede utilizar el compilador de configuración de tabla de comandos basado en XML, *Vsct.exe*, para generar un archivo a partir de un archivo *.ctc* existente.

- Puede usar *Vsct.exe* para generar un archivo *.vsct* a partir de un archivo *.cto* existente.

- Puede crear manualmente un nuevo archivo *.vsct.*

  En este artículo se explica cómo crear manualmente un nuevo archivo *.vsct.*

### <a name="to-manually-create-a-new-vsct-file"></a>Para crear manualmente un nuevo archivo .vsct

1. Inicie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

2. En el menú **Archivo** , elija **Nuevo**y haga clic en **Archivo**.

3. En **el** plantillas panel, haga clic en **archivo XML** y, a continuación, haga clic en **abrir**.

4. En el menú **Ver,** haga clic en **Propiedades** para mostrar las propiedades del archivo XML.

5. En el **propiedades** ventana, haga clic en el **examinar** botón en el **esquemas** propiedad.

6. En la lista de esquemas XSD, seleccione el esquema *vsct.xsd.* Si no está en la lista, haga clic en **Agregar** y, a continuación, busque el archivo en una unidad local. Haga clic en **Aceptar** cuando haya terminado.

7. En el archivo XML, escriba *<CommandTable* y, a continuación, presione **Tab**. Cierre la etiqueta *>* escribiendo .

    Esta acción crea un archivo *.vsct* básico.

8. Rellene los elementos del archivo XML que desea agregar, según la referencia de esquema XML de [VSCT.](../../extensibility/vsct-xml-schema-reference.md) Para obtener más información, consulte [Crear archivos .vsct](../../extensibility/internals/authoring-dot-vsct-files.md).

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Cómo: Crear un archivo .vsct a partir de un archivo .ctc existente

Puede crear un archivo *.vsct* basado en XML a partir de un archivo de origen *.ctc* de tabla de comandos existente. Al hacerlo, puede aprovechar las ventajas del nuevo basado formato del compilador de la tabla de comandos (VSCT) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Para crear un archivo .vsct a partir de un archivo .ctc existente

1. Obtenga una copia del lenguaje Perl.

2. Obtenga una copia de la *ConvertCTCToVSCT.pl*de secuencia de comandos de Perl , que normalmente se encuentra en la * \<ruta* de instalación del SDK de Visual Studio> carpeta .VisualStudioIntegration .

3. Obtenga una copia del archivo de origen *.ctc* que desea convertir.

4. Coloque los archivos en el mismo directorio.

5. En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la ventana del símbolo del sistema, vaya al directorio.

6. Tipo

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    donde *PkgCmd.ctc* es el nombre del archivo *.ctc* y *PkgCmd.vsct* es el nombre del archivo *.vsct* que desea crear.

    Esta acción crea un nuevo archivo de origen de tabla de comandos *XML .vsct.* Puede compilar el archivo mediante *Vsct.exe*, el compilador VSCT, como lo haría con cualquier otro archivo *.vsct.*

   > [!NOTE]
   > Puede mejorar la legibilidad del archivo *.vsct* reformateando los comentarios XML.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Cómo: Crear un archivo .vsct a partir de un archivo .cto existente

Puede crear un archivo *.vsct* basado en XML a partir de un archivo *.cto* binario existente. Si lo hace, podrá aprovechar el nuevo formato de compilador de tabla de comandos. Este proceso funciona incluso si el archivo *.cto* se compiló a partir de un archivo *.ctc.* Puede editar y compilar el archivo *.vsct* en otro archivo .cto.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Para crear un archivo .vsct a partir de un archivo .cto

1. Obtenga copias del archivo *.cto* y su archivo *.ctsym* correspondiente.

2. Coloque los archivos en el mismo directorio que el compilador *vsct.exe.*

3. En el símbolo del sistema de Visual Studio, vaya al directorio que contiene los archivos *.cto* y *.ctsym.*

4. Tipo

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     donde \<\> ctofilename es el nombre del \<archivo\> *.cto,* vsctfilename es el nombre del \<archivo *.vsct* que desea crear y symfilename\> es el nombre del archivo *.ctsym.*

     Este proceso crea un nuevo archivo del compilador de tabla de comandos *XML .vsct.* Puede editar y compilar el archivo con *vsct.exe*, el compilador vsct, como lo haría con cualquier otro archivo *.vsct.*

## <a name="compile-the-code"></a>Compilar el código
 Simplemente agregar un archivo *.vsct* a un proyecto no hace que se compile. Debe incorporarlo en el proceso de compilación.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>Para agregar un archivo .vsct a la compilación del proyecto

1. Abra el archivo de proyecto en el editor. Si se carga el proyecto, primero debe descargarlo.

2. Agregue un [elemento ItemGroup](../../msbuild/itemgroup-element-msbuild.md) que contenga un `VSCTCompile` elemento, como se muestra en el ejemplo siguiente.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     El `ResourceName` elemento siempre debe `Menus.ctmenu`establecerse en .

3. Si el proyecto contiene un archivo *.resx,* agregue un `EmbeddedResource` elemento que contenga un `MergeWithCTO` elemento, como se muestra en el ejemplo siguiente:

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Este marcado debe `ItemGroup` ir dentro del elemento que contiene recursos incrustados.

4. Abra el archivo de paquete, normalmente denominado * \<ProjectName\>Package.cs* o * \<ProjectName\>Package.vb*, en el editor.

5. Agregue `ProvideMenuResource` un atributo a la clase de paquete, como se muestra en el ejemplo siguiente.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     El primer valor del parámetro `ResourceName` debe coincidir con el valor del atributo definido en el archivo de proyecto.

## <a name="see-also"></a>Vea también
- [Crear archivos .vsct](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Archivos de tabla de comandos de Visual Studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Referencia de esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)
