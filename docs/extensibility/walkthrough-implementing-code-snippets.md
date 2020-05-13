---
title: 'Tutorial: Implementación de fragmentos de código ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: ba1b6e0852c1ec1b306938b791eed78e79d211ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697094"
---
# <a name="walkthrough-implement-code-snippets"></a>Tutorial: Implementar fragmentos de código
Puede crear fragmentos de código e incluirlos en una extensión de editor para que los usuarios de la extensión puedan agregarlos a su propio código.

 Un fragmento de código es un fragmento de código u otro texto que se puede incorporar en un archivo. Para ver todos los fragmentos de código que se han registrado para determinados lenguajes de programación, en el menú **Herramientas,** haga clic en Administrador de **fragmentos**de código . Para insertar un fragmento de código en un archivo, haga clic con el botón derecho en el lugar donde desee el fragmento de código, haga clic en Insertar fragmento de código o **Rodear con**, busque el fragmento de código que desee y, a continuación, haga doble clic en él. Pulse **Tab** o **Shift**+**Tab** para modificar las partes relevantes del fragmento de código y, a continuación, pulse **Intro** o **Esc** para aceptarlo. Para obtener más información, consulte [Fragmentos](../ide/code-snippets.md)de código .

 Un fragmento de código está contenido en un archivo XML que tiene la extensión de nombre de archivo .snippet*. Un fragmento de código puede contener campos que se resaltan después de insertar el fragmento de código para que el usuario pueda encontrarlos y cambiarlos. Un archivo de fragmento de código también proporciona información para el Administrador de **fragmentos** de código para que pueda mostrar el nombre del fragmento de código en la categoría correcta. Para obtener información sobre el esquema de fragmento de código, vea Referencia de esquema de [fragmentos](../ide/code-snippets-schema-reference.md)de código .

 Este tutorial enseña cómo realizar estas tareas:

1. Crear y registrar fragmentos de código para un idioma específico.

2. Agregue el comando **Insertar fragmento de código** a un menú contextual.

3. Implementar la expansión de fragmentos de código.

   Este tutorial se basa en [Tutorial: Mostrar finalización](../extensibility/walkthrough-displaying-statement-completion.md)de instrucciones .

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-and-register-code-snippets"></a>Crear y registrar fragmentos de código
 Normalmente, los fragmentos de código están asociados a un servicio de lenguaje registrado. Sin embargo, no es <xref:Microsoft.VisualStudio.Package.LanguageService> necesario implementar a para registrar fragmentos de código. En su lugar, solo especifique un GUID en el <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> archivo de índice de fragmento de código y, a continuación, use el mismo GUID en el que agregue al proyecto.

 En los pasos siguientes se muestra cómo crear fragmentos de código y asociarlos a un GUID específico.

1. Cree la siguiente estructura de directorios:

    **%InstallDir%-TestSnippets-Snippets-1033\\**

    donde *%InstallDir%* es la carpeta de instalación de Visual Studio. (Aunque esta ruta de acceso se utiliza normalmente para instalar fragmentos de código, puede especificar cualquier ruta de acceso.)

2. En la carpeta .1033, cree un archivo *.xml* y asímóquele **TestSnippets.xml**. (Aunque este nombre se utiliza normalmente para un archivo de índice de fragmento de código, puede especificar cualquier nombre siempre que tenga una extensión de nombre de archivo *.xml.)* Agregue el texto siguiente y, a continuación, elimine el GUID de marcador de posición y agregue el suyo propio.

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

3. Cree un archivo en la carpeta de fragmentos de código, asígnelo **test**`.snippet`y, a continuación, agregue el texto siguiente:

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

   Los pasos siguientes muestran cómo registrar los fragmentos de código.

### <a name="to-register-code-snippets-for-a-specific-guid"></a>Para registrar fragmentos de código para un GUID específico

1. Abra el proyecto **CompletionTest.** Para obtener información sobre cómo crear este proyecto, vea [Tutorial: Mostrar finalización](../extensibility/walkthrough-displaying-statement-completion.md)de instrucciones .

2. En el proyecto, agregue referencias a los ensamblados siguientes:

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.TextManager.Interop.8.0

    - microsoft.msxml

3. En el proyecto, abra el archivo **source.extension.vsixmanifest.**

4. Asegúrese de que la pestaña **Activos** contiene un tipo de contenido **VsPackage** y que **Project** se establece en el nombre del proyecto.

5. Seleccione el proyecto CompletionTest y, en la ventana Propiedades, establezca **Generar archivo Pkgdef** en **true**. Guarde el proyecto.

6. Agregue una `SnippetUtilities` clase estática al proyecto.

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. En la clase SnippetUtilities, defina un GUID y asíbse con el valor que usó en el archivo *SnippetsIndex.xml.*

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. Agregue <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> el `TestCompletionHandler` a la clase. Este atributo se puede agregar a cualquier clase pública o interna (no estática) del proyecto. (Es posible que `using` tenga que agregar una directiva para el Microsoft.VisualStudio.Shell espacio de nombres.)

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. Compile y ejecute el proyecto. En la instancia experimental de Visual Studio que se inicia cuando se ejecuta el proyecto, el fragmento de código que acaba de registrar debe mostrarse en el Administrador de **fragmentos** de código en el lenguaje **TestSnippets.**

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Agregue el comando Insertar fragmento de código al menú contextual
 El comando **Insertar fragmento** de código no se incluye en el menú contextual de un archivo de texto. Por lo tanto, debe habilitar el comando.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Para agregar el comando Insertar fragmento de código al menú contextual

1. Abra `TestCompletionCommandHandler` el archivo de clase.

     Dado que esta <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>clase implementa , puede activar <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> el comando Insertar **fragmento** de código en el método. Antes de habilitar el comando, compruebe que no se llama a este método dentro de una función de automatización porque cuando se hace clic en el comando **Insertar fragmento** de código, muestra la interfaz de usuario (UI) del selector de fragmentos de código.

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. Compile y ejecute el proyecto. En la instancia experimental, abra un archivo que tenga la extensión de nombre de archivo *.zzz* y, a continuación, haga clic con el botón derecho en cualquier lugar. El comando **Insertar fragmento** de código debe aparecer en el menú contextual.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Implementar la expansión de fragmentos de código en la interfaz de usuario del selector de fragmentos de código
 En esta sección se muestra cómo implementar la expansión de fragmentos de código para que se muestre la interfaz de usuario del selector de fragmentos de código cuando se haga clic en **Insertar fragmento** de código en el menú contextual. Un fragmento de código también se expande cuando un usuario escribe el acceso directo de fragmento de código y, a continuación, presiona **Tab**.

 Para mostrar la interfaz de usuario del selector de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> fragmentos de código y habilitar la navegación y la aceptación del fragmento de código posterior a la inserción, utilice el método. El método controla la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> inserción en sí.

 La implementación de la <xref:Microsoft.VisualStudio.TextManager.Interop> expansión de fragmentos de código utiliza interfaces heredadas. Al traducir de las clases de editor actuales al código heredado, recuerde que las interfaces heredadas usan una combinación de números de línea y números de columna para especificar ubicaciones en un búfer de texto, pero las clases actuales usan un índice. Por lo tanto, si un búfer tiene tres líneas cada una de las cuales tiene 10 caracteres (más una nueva línea, que cuenta como un carácter), el cuarto carácter de la tercera línea está en la posición 27 de la implementación actual, pero está en la línea 2, posición 3 en la implementación anterior.

#### <a name="to-implement-snippet-expansion"></a>Para implementar la expansión de fragmentos de código

1. Para el archivo `TestCompletionCommandHandler` que contiene la `using` clase, agregue las siguientes directivas.

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. Haga `TestCompletionCommandHandler` que la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> clase implemente la interfaz.

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. En `TestCompletionCommandHandlerProvider` la clase, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>importe el archivo .

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. Agregue algunos campos privados para las <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>interfaces de expansión de código y el archivo .

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. En el constructor `TestCompletionCommandHandler` de la clase, establezca los siguientes campos.

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. Para mostrar el selector de fragmentos de código cuando el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> usuario hace clic en el comando Insertar **fragmento** de código, agregue el código siguiente al método. (Para que esta explicación `Exec()`sea más legible, no se muestra el código que se usa para la finalización de instrucciones; en su lugar, los bloques de código se agregan al método existente.) Agregue el siguiente bloque de código después del código que comprueba si hay un carácter.

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. Si un fragmento de código tiene campos que se pueden navegar, la sesión de expansión se mantiene abierta hasta que se acepte explícitamente la expansión; si el fragmento de código no tiene campos, la sesión se cierra y se devuelve como `null` por el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> método. En <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> el método, después del código de interfaz de usuario del selector de fragmentos de código que agregó en el paso anterior, agregue el código siguiente para controlar la navegación de fragmentos de código (cuando el usuario presiona **Tab** o **Shift**+**Tab** después de la inserción del fragmento de código).

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. Para insertar el fragmento de código cuando el **Tab**usuario escribe el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> acceso directo correspondiente y, a continuación, presiona Tab , agregue código al método. El método privado que inserta el fragmento de código se mostrará en un paso posterior. Agregue el código siguiente después del código de navegación que agregó en el paso anterior.

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. Implemente los métodos de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfaz. En esta implementación, los <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> únicos métodos de interés son y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Los otros métodos <xref:Microsoft.VisualStudio.VSConstants.S_OK>solo deben devolver .

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. Implemente el método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. El método auxiliar que realmente inserta las expansiones se trata en un paso posterior. La <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> información de línea y columna proporciona, que puede obtener de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. El siguiente método privado inserta un fragmento de código, basado en el acceso directo o en el título y la ruta de acceso. A continuación, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> llama al método con el fragmento de código.

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>Crear y probar la expansión del fragmento de código
 Puede probar si la expansión de fragmentos de código funciona en el proyecto.

1. Compile la solución. Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.

2. Abra un archivo de texto y escriba algo de texto.

3. Haga clic con el botón derecho en algún lugar del texto y, a continuación, haga clic en **Insertar fragmento**de código .

4. La interfaz de usuario del selector de fragmentos de código debe aparecer con una ventana emergente que diga Campos de **reemplazo de prueba**. Haga doble clic en la ventana emergente.

     Se debe insertar el siguiente fragmento de código.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     No pulse **Intro** o **Esc**.

5. Pulse **Tab** y **Shift**+**Tab** para alternar entre "first" y "second".

6. Acepte la inserción pulsando **Intro** o **Esc**.

7. En una parte diferente del texto, escriba "test" y, a continuación, presione **Tab**. Dado que "test" es el acceso directo de fragmento de código, el fragmento de código debe insertarse de nuevo.

## <a name="next-steps"></a>Pasos siguientes
