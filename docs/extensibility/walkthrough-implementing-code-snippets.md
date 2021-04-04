---
title: 'Tutorial: implementar fragmentos de código | Microsoft Docs'
description: Puede crear fragmentos de código e incluirlos en una extensión de editor. Aprenda a crear y registrar fragmentos de código mediante este tutorial.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: leslierichardson95
ms.author: lerich
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: b21a7515f7ad4bad74088b6b580a4a3122a2e12a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216987"
---
# <a name="walkthrough-implement-code-snippets"></a>Tutorial: implementar fragmentos de código
Puede crear fragmentos de código e incluirlos en una extensión de editor para que los usuarios de la extensión puedan agregarlos a su propio código.

 Un fragmento de código es un fragmento de código u otro texto que se puede incorporar en un archivo. Para ver todos los fragmentos de código que se han registrado para lenguajes de programación concretos, en el menú **herramientas** , haga clic en **Administrador de fragmentos de código**. Para insertar un fragmento de código en un archivo, haga clic con el botón secundario en el lugar en el que desea incluirlo, haga clic en Insertar fragmento de código o **delimitar con**, busque el fragmento de código que desee y, a continuación, haga doble clic en él. Presione **Tab** o **MAYÚS** + **Tab** para modificar las partes pertinentes del fragmento de código y, a continuación, presione **entrar** o **ESC** para aceptarla. Para obtener más información, vea [fragmentos de código](../ide/code-snippets.md).

 Un fragmento de código se encuentra en un archivo XML que tiene la extensión de nombre de archivo. snippet *. Un fragmento de código puede contener campos que se resaltan después de insertar el fragmento de código para que el usuario pueda buscarlos y cambiarlos. Un archivo de fragmento de código también proporciona información para el **Administrador de fragmentos de código** , de modo que pueda mostrar el nombre del fragmento de código en la categoría correcta. Para obtener información sobre el esquema de fragmentos de código, vea [referencia de esquemas de fragmentos de código](../ide/code-snippets-schema-reference.md).

 En este tutorial se enseña cómo realizar estas tareas:

1. Crear y registrar fragmentos de código para un idioma específico.

2. Agregue el comando **Insertar fragmento de código** a un menú contextual.

3. Implementar la expansión de fragmentos de código.

   Este tutorial se basa en el [Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md).

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-and-register-code-snippets"></a>Crear y registrar fragmentos de código
 Normalmente, los fragmentos de código están asociados a un servicio de lenguaje registrado. Sin embargo, no es necesario implementar un <xref:Microsoft.VisualStudio.Package.LanguageService> para registrar fragmentos de código. En su lugar, solo tiene que especificar un GUID en el archivo de índice de fragmento de código y, a continuación, usar el mismo GUID en el <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> que agregue al proyecto.

 En los pasos siguientes se muestra cómo crear fragmentos de código y asociarlos a un GUID específico.

1. Cree la siguiente estructura de directorios:

    **%InstallDir%\TestSnippets\Snippets\1033\\**

    donde *% INSTALLDIR%* es la carpeta de instalación de Visual Studio. (Aunque esta ruta de acceso se usa normalmente para instalar fragmentos de código, puede especificar cualquier ruta de acceso).

2. En la carpeta \ 1033 \, cree un archivo *. XML* y asígnele el nombre **TestSnippets.xml**. (Aunque este nombre se usa normalmente para un archivo de índice de fragmento de código, puede especificar cualquier nombre siempre que tenga una extensión de nombre de archivo *. XML* ). Agregue el siguiente texto y, a continuación, elimine el GUID del marcador de posición y agregue el suyo propio.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <SnippetCollection>
       <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}">
           <SnippetDir>
               <OnOff>On</OnOff>
               <Installed>true</Installed>
               <Locale>1033</Locale>
               <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath>
               <LocalizedName>Snippets</LocalizedName>
           </SnippetDir>
       </Language>
   </SnippetCollection>
   ```

3. Cree un archivo en la carpeta snippet, asígnele el nombre **Test** `.snippet` y, a continuación, agregue el siguiente texto:

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
       <CodeSnippet Format="1.0.0">
           <Header>
               <Title>Test replacement fields</Title>
               <Shortcut>test</Shortcut>
               <Description>Code snippet for testing replacement fields</Description>
               <Author>MSIT</Author>
               <SnippetTypes>
                   <SnippetType>Expansion</SnippetType>
               </SnippetTypes>
           </Header>
           <Snippet>
               <Declarations>
                   <Literal>
                     <ID>param1</ID>
                       <ToolTip>First field</ToolTip>
                       <Default>first</Default>
                   </Literal>
                   <Literal>
                       <ID>param2</ID>
                       <ToolTip>Second field</ToolTip>
                       <Default>second</Default>
                   </Literal>
               </Declarations>
               <References>
                  <Reference>
                      <Assembly>System.Windows.Forms.dll</Assembly>
                  </Reference>
               </References>
               <Code Language="TestSnippets">
                   <![CDATA[MessageBox.Show("$param1$");
        MessageBox.Show("$param2$");]]>
               </Code>
           </Snippet>
       </CodeSnippet>
   </CodeSnippets>
   ```

   En los pasos siguientes se muestra cómo registrar los fragmentos de código.

### <a name="to-register-code-snippets-for-a-specific-guid"></a>Para registrar fragmentos de código para un GUID específico

1. Abra el proyecto **CompletionTest** . Para obtener información sobre cómo crear este proyecto, vea [Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md).

2. En el proyecto, agregue referencias a los siguientes ensamblados:

    - Microsoft. VisualStudio. TextManager. Interop

    - Microsoft. VisualStudio. TextManager. Interop. 8.0

    - Microsoft. MSXML

3. En el proyecto, abra el archivo **source. Extension. vsixmanifest** .

4. Asegúrese de que la pestaña **activos** contiene un tipo de contenido de **VsPackage** y que el **proyecto** está establecido en el nombre del proyecto.

5. Seleccione el proyecto CompletionTest y, en el ventana Propiedades establezca **generar archivo Pkgdef** en **true**. Guarde el proyecto.

6. Agregue una `SnippetUtilities` clase estática al proyecto.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet22":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet22":::

7. En la clase SnippetUtilities, defina un GUID y asígnele el valor que usó en el archivo de *SnippetsIndex.xml* .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet23":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet23":::

8. Agregue <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> a la `TestCompletionHandler` clase. Este atributo se puede Agregar a cualquier clase pública o interna (no estática) del proyecto. (Es posible que tenga que agregar una `using` Directiva para el espacio de nombres Microsoft. VisualStudio. Shell).

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet24":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet24":::

9. Compile y ejecute el proyecto. En la instancia experimental de Visual Studio que se inicia cuando se ejecuta el proyecto, el fragmento de código que acaba de registrar se debe mostrar en el **Administrador de fragmentos de código** en el lenguaje **TestSnippets** .

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Agregar el comando Insertar fragmento de código al menú contextual
 El comando **Insertar fragmento de código** no se incluye en el menú contextual de un archivo de texto. Por lo tanto, debe habilitar el comando.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Para agregar el comando Insertar fragmento de código al menú contextual

1. Abra el `TestCompletionCommandHandler` archivo de clase.

     Dado que esta clase implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , puede activar el comando **Insertar fragmento de código** en el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método. Antes de habilitar el comando, compruebe que no se llama a este método dentro de una función de automatización porque, cuando se hace clic en el comando **Insertar fragmento de código** , se muestra la interfaz de usuario del selector de fragmentos de código.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet25":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet25":::

2. Compile y ejecute el proyecto. En la instancia experimental, abra un archivo que tenga la extensión de nombre de archivo *. zzz* y, a continuación, haga clic con el botón secundario en cualquier parte de él. El comando **Insertar fragmento de código** debe aparecer en el menú contextual.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Implementar la expansión de fragmentos de código en la interfaz de usuario del selector de fragmentos de código
 En esta sección se muestra cómo implementar la expansión de fragmentos de código para que se muestre la interfaz de usuario del selector de fragmentos al hacer clic en **Insertar fragmento** de código en el menú contextual. Un fragmento de código también se expande cuando un usuario escribe el acceso directo del fragmento de código y, a continuación, presiona la **tecla TAB**.

 Para mostrar la interfaz de usuario del selector de fragmentos de código y habilitar la navegación y la aceptación del fragmento de código posterior a la inserción, use el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método. El método controla la propia inserción <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> .

 La implementación de la expansión de fragmentos de código usa interfaces heredadas <xref:Microsoft.VisualStudio.TextManager.Interop> . Cuando traduzca de las clases de editor actuales al código heredado, recuerde que las interfaces heredadas usan una combinación de números de línea y de columna para especificar las ubicaciones en un búfer de texto, pero las clases actuales usan un índice. Por lo tanto, si un búfer tiene tres líneas, cada una de las cuales tiene 10 caracteres (más una nueva línea, que cuenta como un carácter), el cuarto carácter de la tercera línea está en la posición 27 de la implementación actual, pero está en la línea 2, posición 3 en la implementación anterior.

#### <a name="to-implement-snippet-expansion"></a>Para implementar la expansión de fragmentos de código

1. Agregue las siguientes directivas al archivo que contiene la `TestCompletionCommandHandler` clase `using` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet26":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet26":::

2. Haga que la `TestCompletionCommandHandler` clase implemente la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfaz.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet27":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet27":::

3. En la `TestCompletionCommandHandlerProvider` clase, importe <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet28":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet28":::

4. Agregue algunos campos privados para las interfaces de expansión de código y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet29":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet29":::

5. En el constructor de la `TestCompletionCommandHandler` clase, establezca los campos siguientes.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet30":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet30":::

6. Para mostrar el selector de fragmentos de código cuando el usuario hace clic en el comando **Insertar fragmento** , agregue el código siguiente al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método. (Para que esta explicación sea más legible, `Exec()` no se muestra el código que se utiliza para la finalización de instrucciones; en su lugar, se agregan bloques de código al método existente). Agregue el siguiente bloque de código después del código que comprueba un carácter.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet31":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet31":::

7. Si un fragmento de código tiene campos a los que se puede navegar, la sesión de expansión se mantiene abierta hasta que se acepta explícitamente la expansión; Si el fragmento de código no tiene campos, la sesión se cierra y se devuelve como `null` el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> método. En el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método, después del código de la interfaz de usuario del selector de fragmentos de código que agregó en el paso anterior, agregue el código siguiente para controlar la navegación por fragmentos de código (cuando el usuario presiona la tecla **Tab** o **MAYÚS** después de la +  inserción del fragmento de código).

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet32":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet32":::

8. Para insertar el fragmento de código cuando el usuario escribe el acceso directo correspondiente y, a continuación, presiona **Tab**, agregue código al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método. El método privado que inserta el fragmento de código se mostrará en un paso posterior. Agregue el código siguiente después del código de navegación que agregó en el paso anterior.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet33":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet33":::

9. Implemente los métodos de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfaz. En esta implementación, los únicos métodos de interés son <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> . Los otros métodos deben devolver simplemente <xref:Microsoft.VisualStudio.VSConstants.S_OK> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet34":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet34":::

10. Implemente el método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. El método auxiliar que realmente inserta las expansiones se trata en un paso posterior. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>Proporciona información de línea y de columna, que se puede obtener de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet35":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet35":::

11. El siguiente método privado inserta un fragmento de código, basado en el método abreviado o en el título y la ruta de acceso. A continuación, llama al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> método con el fragmento de código.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet36":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet36":::

## <a name="build-and-test-code-snippet-expansion"></a>Expansión de fragmentos de código de compilación y prueba
 Puede comprobar si la expansión de fragmentos de código funciona en el proyecto.

1. Compile la solución. Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.

2. Abra un archivo de texto y escriba algún texto.

3. Haga clic con el botón secundario en algún lugar del texto y haga clic en **Insertar fragmento de código**.

4. La interfaz de usuario del selector de fragmentos de código debe aparecer con un elemento emergente que indica **los campos de sustitución de prueba**. Haga doble clic en el elemento emergente.

     Se debe insertar el siguiente fragmento de código.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     No presione **entrar** o **ESC**.

5. Presione **Tab** y **MAYÚS** + **Tab** para alternar entre "primero" y "segundo".

6. Presione **entrar** o **ESC** para aceptar la inserción.

7. En otra parte del texto, escriba "Test" y, a continuación, presione **Tab**. Dado que "Test" es el acceso directo del fragmento de código, se debe volver a insertar el fragmento de código.

## <a name="next-steps"></a>Pasos siguientes
