---
title: 'Cómo: crear un. Archivo Vsct | Microsoft Docs'
description: Obtenga información sobre cómo crear manualmente un archivo. Vsct, un archivo de configuración de tabla de comandos de Visual Studio basado en XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 47d38e68494f29947131bcc8ce3a2a59b2e8d48b
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480374"
---
# <a name="how-to-create-a-vsct-file"></a>Cómo: crear un archivo. Vsct

Hay varias maneras de crear un archivo de configuración de tabla de comandos de Visual Studio (*. Vsct*) basado en XML.

- Puede crear un nuevo VSPackage en la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plantilla de paquete.

- Puede usar el compilador de configuración de tabla de comandos basado en XML, *Vsct.exe*, para generar un archivo a partir de un archivo *. CTC* existente.

- Puede usar *Vsct.exe* para generar un archivo *. Vsct* a partir de un archivo *. CTO* existente.

- Puede crear un nuevo archivo *. Vsct* de forma manual.

  En este artículo se explica cómo crear manualmente un nuevo archivo *. Vsct* .

### <a name="to-manually-create-a-new-vsct-file"></a>Para crear manualmente un nuevo archivo. Vsct

1. Inicie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

2. En el menú **Archivo** , elija **Nuevo** y haga clic en **Archivo**.

3. En el panel **plantillas** , haga clic en **archivo XML** y, a continuación, haga clic en **abrir**.

4. En el menú **Ver** , haga clic en **propiedades** para mostrar las propiedades del archivo XML.

5. En la ventana **propiedades** , haga clic en el botón **examinar** de la propiedad **esquemas** .

6. En la lista de esquemas XSD, seleccione el esquema *Vsct. xsd* . Si no está en la lista, haga clic en **Agregar** y, a continuación, busque el archivo en una unidad local. Cuando haya terminado, haga clic en **Aceptar** .

7. En el archivo XML, escriba *<CommandTable* y, a continuación, presione **Tab**. Cierre la etiqueta escribiendo *>* .

    Esta acción crea un archivo *. Vsct* básico.

8. Rellene los elementos del archivo XML que desea agregar, de acuerdo con la referencia del [esquema XML VSCT](../../extensibility/vsct-xml-schema-reference.md). Para obtener más información, consulte [Author. Vsct files](../../extensibility/internals/authoring-dot-vsct-files.md).

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Cómo: crear un archivo. Vsct a partir de un archivo. CTC existente

Puede crear un archivo *. Vsct* basado en XML a partir de un archivo de origen de tabla de comandos existente *. CTC* . Al hacerlo, puede aprovechar las ventajas del nuevo basado formato del compilador de la tabla de comandos (VSCT) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Para crear un archivo .vsct a partir de un archivo .ctc existente

1. Obtenga una copia del lenguaje Perl.

2. Obtenga una copia del script Perl *ConvertCTCToVSCT.pl*, que normalmente se encuentra en la carpeta *\<Visual Studio SDK installation path> \VisualStudioIntegration\Tools\bin* .

3. Obtenga una copia del archivo de origen *. CTC* que desea convertir.

4. Coloque los archivos en el mismo directorio.

5. En la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ventana del símbolo del sistema, navegue hasta el directorio.

6. Tipo

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    donde *PkgCmd. CTC* es el nombre del archivo *. CTC* y *PkgCmd. Vsct* es el nombre del archivo *. Vsct* que desea crear.

    Esta acción crea un nuevo archivo de origen de tabla de comandos XML *. Vsct* . Puede compilar el archivo mediante *Vsct.exe*, el compilador VSCT, como haría con cualquier otro archivo *. VSCT* .

   > [!NOTE]
   > Puede mejorar la legibilidad del archivo *. Vsct* reformateando los comentarios XML.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Cómo: crear un archivo. Vsct a partir de un archivo. CTO existente

Puede crear un archivo *. Vsct* basado en XML a partir de un archivo *. CTO* binario existente. Si lo hace, podrá aprovechar el nuevo formato de compilador de tabla de comandos. Este proceso funciona aunque el archivo *. CTO* se haya compilado a partir de un archivo *. CTC* . Puede editar y compilar el archivo *. Vsct* en otro archivo. CTO.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Para crear un archivo .vsct a partir de un archivo .cto

1. Obtenga copias del archivo *. CTO* y su archivo *. ctsym* correspondiente.

2. Coloque los archivos en el mismo directorio que el compilador *vsct.exe* .

3. En el símbolo del sistema de Visual Studio, vaya al directorio que contiene los archivos *. CTO* y *. ctsym* .

4. Tipo

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     donde \<ctofilename\> es el nombre del archivo *. CTO* , \<vsctfilename\> es el nombre del archivo *. Vsct* que desea crear y \<symfilename\> es el nombre del archivo *. ctsym* .

     Este proceso crea un nuevo archivo de compilador de tabla de comandos XML *. Vsct* . Puede editar y compilar el archivo con *vsct.exe*, el compilador Vsct, como haría con cualquier otro archivo *. Vsct* .

## <a name="compile-the-code"></a>Compilar el código
 Simplemente agregar un archivo *. Vsct* a un proyecto no hace que se compile. Debe incorporarlo en el proceso de compilación.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>Para agregar un archivo. Vsct a la compilación del proyecto

1. Abra el archivo de proyecto en el editor. Si el proyecto está cargado, debe descargarlo primero.

2. Agregue un [elemento ItemGroup](../../msbuild/itemgroup-element-msbuild.md) que contenga un `VSCTCompile` elemento, como se muestra en el ejemplo siguiente.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     El `ResourceName` elemento siempre debe establecerse en `Menus.ctmenu` .

3. Si el proyecto contiene un archivo *. resx* , agregue un `EmbeddedResource` elemento que contenga un `MergeWithCTO` elemento, como se muestra en el ejemplo siguiente:

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Este marcado debe ir dentro del `ItemGroup` elemento que contiene recursos incrustados.

4. Abra el archivo de paquete, normalmente denominado *\<ProjectName\> Package.CS* o *\<ProjectName\> Package. VB*, en el editor.

5. Agregue un `ProvideMenuResource` atributo a la clase de paquete, como se muestra en el ejemplo siguiente.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     El primer valor de parámetro debe coincidir con el valor del `ResourceName` atributo definido en el archivo de proyecto.

## <a name="see-also"></a>Consulte también
- [Archivos Author. Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Archivos de tabla de comandos de Visual Studio (. Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)
