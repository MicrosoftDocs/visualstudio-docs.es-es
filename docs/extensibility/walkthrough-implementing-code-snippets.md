---
title: 'Tutorial: implementar fragmentos de código | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: madskristensen
ms.author: madsk
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 84674a12165a3c5cd47c9004274669d377d330c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632509"
---
# <a name="walkthrough-implement-code-snippets"></a>Tutorial: implementar fragmentos de código
Puede crear fragmentos de código e incluirlos en una extensión de editor para que los usuarios de la extensión puedan agregarlos a su propio código.

 Un fragmento de código es un fragmento de código u otro texto que se puede incorporar en un archivo. Para ver todos los fragmentos de código que se han registrado para lenguajes de programación concretos, en el menú **herramientas** , haga clic en **Administrador de fragmentos de código**. Para insertar un fragmento de código en un archivo, haga clic con el botón secundario en el lugar en el que desea incluirlo, haga clic en Insertar fragmento de código o **delimitar con**, busque el fragmento de código que desee y, a continuación, haga doble clic en él. Presione **Tab** o **MAYÚS** +**Tab** para modificar las partes pertinentes del fragmento de código y, a continuación, presione **entrar** o **ESC** para aceptarla. Para obtener más información, vea [fragmentos de código](../ide/code-snippets.md).

 Un fragmento de código se encuentra en un archivo XML que tiene la extensión de nombre de archivo. snippet *. Un fragmento de código puede contener campos que se resaltan después de insertar el fragmento de código para que el usuario pueda buscarlos y cambiarlos. Un archivo de fragmento de código también proporciona información para el **Administrador de fragmentos de código** , de modo que pueda mostrar el nombre del fragmento de código en la categoría correcta. Para obtener información sobre el esquema de fragmentos de código, vea [referencia de esquemas de fragmentos de código](../ide/code-snippets-schema-reference.md).

 En este tutorial se enseña cómo realizar estas tareas:

1. Crear y registrar fragmentos de código para un idioma específico.

2. Agregue el comando **Insertar fragmento de código** a un menú contextual.

3. Implementar la expansión de fragmentos de código.

   Este tutorial se basa en el [Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md).

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-and-register-code-snippets"></a>Crear y registrar fragmentos de código
 Normalmente, los fragmentos de código están asociados a un servicio de lenguaje registrado. Sin embargo, no es necesario implementar un <xref:Microsoft.VisualStudio.Package.LanguageService> para registrar fragmentos de código. En su lugar, solo tiene que especificar un GUID en el archivo de índice de fragmento de código y, a continuación, usar el mismo GUID en el <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> que agregue al proyecto.

 En los pasos siguientes se muestra cómo crear fragmentos de código y asociarlos a un GUID específico.

1. Cree la siguiente estructura de directorios:

    **@No__t_1%InstallDir%\TestSnippets\Snippets\1033**

    donde *% INSTALLDIR%* es la carpeta de instalación de Visual Studio. (Aunque esta ruta de acceso se usa normalmente para instalar fragmentos de código, puede especificar cualquier ruta de acceso).

2. En la carpeta \ 1033 \, cree un archivo *. XML* y asígnele el nombre **TestSnippets. XML**. (Aunque este nombre se usa normalmente para un archivo de índice de fragmento de código, puede especificar cualquier nombre siempre que tenga una extensión de nombre de archivo *. XML* ). Agregue el siguiente texto y, a continuación, elimine el GUID del marcador de posición y agregue el suyo propio.

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

3. Cree un archivo en la carpeta de fragmentos de código, asígnele el nombre **test** `.snippet` y, a continuación, agregue el siguiente texto:

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

6. Agregue una clase de `SnippetUtilities` estática al proyecto.

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. En la clase SnippetUtilities, defina un GUID y asígnele el valor que usó en el archivo *SnippetsIndex. XML* .

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. Agregue el <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> a la clase `TestCompletionHandler`. Este atributo se puede Agregar a cualquier clase pública o interna (no estática) del proyecto. (Es posible que tenga que agregar una directiva `using` para el espacio de nombres Microsoft. VisualStudio. Shell).

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. Compile y ejecute el proyecto. En la instancia experimental de Visual Studio que se inicia cuando se ejecuta el proyecto, el fragmento de código que acaba de registrar se debe mostrar en el **Administrador de fragmentos de código** en el lenguaje **TestSnippets** .

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Agregar el comando Insertar fragmento de código al menú contextual
 El comando **Insertar fragmento de código** no se incluye en el menú contextual de un archivo de texto. Por lo tanto, debe habilitar el comando.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Para agregar el comando Insertar fragmento de código al menú contextual

1. Abra el archivo de clase de `TestCompletionCommandHandler`.

     Dado que esta clase implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, puede activar el comando **Insertar fragmento de código** en el método <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>. Antes de habilitar el comando, compruebe que no se llama a este método dentro de una función de automatización porque, cuando se hace clic en el comando **Insertar fragmento de código** , se muestra la interfaz de usuario del selector de fragmentos de código.

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. Compile y ejecute el proyecto. En la instancia experimental, abra un archivo que tenga la extensión de nombre de archivo *. zzz* y, a continuación, haga clic con el botón secundario en cualquier parte de él. El comando **Insertar fragmento de código** debe aparecer en el menú contextual.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Implementar la expansión de fragmentos de código en la interfaz de usuario del selector de fragmentos de código
 En esta sección se muestra cómo implementar la expansión de fragmentos de código para que se muestre la interfaz de usuario del selector de fragmentos al hacer clic en **Insertar fragmento** de código en el menú contextual. Un fragmento de código también se expande cuando un usuario escribe el acceso directo del fragmento de código y, a continuación, presiona la **tecla TAB**.

 Para mostrar la interfaz de usuario del selector de fragmentos de código y habilitar la aceptación del fragmento de navegación y posterior a la inserción, use el método <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. El método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> controla la propia inserción.

 La implementación de la expansión de fragmentos de código utiliza interfaces heredadas de <xref:Microsoft.VisualStudio.TextManager.Interop>. Cuando traduzca de las clases de editor actuales al código heredado, recuerde que las interfaces heredadas usan una combinación de números de línea y de columna para especificar las ubicaciones en un búfer de texto, pero las clases actuales usan un índice. Por lo tanto, si un búfer tiene tres líneas, cada una de las cuales tiene 10 caracteres (más una nueva línea, que cuenta como un carácter), el cuarto carácter de la tercera línea está en la posición 27 de la implementación actual, pero está en la línea 2, posición 3 en la implementación anterior.

#### <a name="to-implement-snippet-expansion"></a>Para implementar la expansión de fragmentos de código

1. Agregue las siguientes directivas de `using` al archivo que contiene la clase `TestCompletionCommandHandler`.

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. Haga que la clase `TestCompletionCommandHandler` implemente la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient>.

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. En la clase `TestCompletionCommandHandlerProvider`, importe el <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. Agregue algunos campos privados para las interfaces de expansión de código y el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. En el constructor de la clase `TestCompletionCommandHandler`, establezca los campos siguientes.

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. Para mostrar el selector de fragmentos de código cuando el usuario hace clic en el comando **Insertar fragmento** , agregue el siguiente código al método <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. (Para que esta explicación sea más legible, no se muestra el `Exec()`code que se utiliza para la finalización de instrucciones; en su lugar, se agregan bloques de código al método existente). Agregue el siguiente bloque de código después del código que comprueba un carácter.

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. Si un fragmento de código tiene campos a los que se puede navegar, la sesión de expansión se mantiene abierta hasta que se acepta explícitamente la expansión; Si el fragmento de código no tiene campos, la sesión se cierra y se devuelve como `null` por el método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A>. En el método <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>, después del código de la interfaz de usuario del selector de fragmentos de código que agregó en el paso anterior, agregue el código siguiente para controlar la navegación por fragmentos de código (cuando el usuario presiona **Tab** o **MAYÚS** +**pestaña** después de la inserción del fragmento de código).

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. Para insertar el fragmento de código cuando el usuario escribe el acceso directo correspondiente y, a continuación, presiona **Tab**, agregue código al método <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. El método privado que inserta el fragmento de código se mostrará en un paso posterior. Agregue el código siguiente después del código de navegación que agregó en el paso anterior.

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. Implemente los métodos de la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient>. En esta implementación, los únicos métodos de interés son <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Los otros métodos solo deben devolver <xref:Microsoft.VisualStudio.VSConstants.S_OK>.

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. Implemente el método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. El método auxiliar que realmente inserta las expansiones se trata en un paso posterior. El <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> proporciona información de línea y de columna, que puede obtener de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. El siguiente método privado inserta un fragmento de código, basado en el método abreviado o en el título y la ruta de acceso. A continuación, llama al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> con el fragmento de código.

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

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

5. Presione **Tab** y **MAYÚS** +**Tab** para alternar entre "primero" y "segundo".

6. Presione **entrar** o **ESC**para aceptar la inserción.

7. En otra parte del texto, escriba "Test" y, a continuación, presione **Tab**. Dado que "Test" es el acceso directo del fragmento de código, se debe volver a insertar el fragmento de código.

## <a name="next-steps"></a>Pasos siguientes
