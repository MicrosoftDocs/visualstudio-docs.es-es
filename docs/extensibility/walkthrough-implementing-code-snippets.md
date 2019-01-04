---
title: 'Tutorial: Implementación de fragmentos de código | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4866f028851fadbee9f8ab5dbd6d4dc50015a728
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902193"
---
# <a name="walkthrough-implement-code-snippets"></a>Tutorial: Implementar los fragmentos de código
Puede crear fragmentos de código e incluirlos en una extensión del editor para que los usuarios de la extensión pueden agregarlas a su propio código.  
  
 Un fragmento de código es un fragmento de código u otro texto que se puede incorporar en un archivo. Para ver todos los fragmentos de código que se han registrado para lenguajes de programación determinados, en el **herramientas** menú, haga clic en **Administrador de fragmentos de código**. Para insertar un fragmento de código en un archivo, contextual donde desea que el fragmento de código, haga clic en Insertar fragmento de código o **rodear con**, localice el fragmento de código que desee y, a continuación, haga doble clic en él. Presione **ficha** o **MAYÚS**+**ficha** para modificar las partes relevantes del fragmento de código y, a continuación, presione **ENTRAR** o **Esc** a aceptarla. Para obtener más información, consulte [fragmentos de código](../ide/code-snippets.md).  
  
 Un fragmento de código se encuentra en un archivo XML que tiene la extensión de nombre de archivo .snippet *. Un fragmento de código puede contener campos que se resaltan después de inserta el fragmento de código para que el usuario pueda buscar y cambiarlos. Un archivo de fragmento de código también proporciona información para el **Administrador de fragmentos de código** para que pueda mostrar el nombre del fragmento de código en la categoría correcta. Para obtener información acerca del esquema del fragmento de código, vea [referencia de esquema de fragmentos de código](../ide/code-snippets-schema-reference.md).  
  
 En este tutorial se enseña cómo realizar estas tareas:  
  
1. Cree y registre los fragmentos de código para un idioma específico.  
  
2. Agregar el **Insertar fragmento de código** comando a un menú contextual.  
  
3. Implementar la expansión del fragmento de código.  
  
   En este tutorial se basa en [Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Ha incluido como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-and-register-code-snippets"></a>Crear y registrar los fragmentos de código  
 Normalmente, los fragmentos de código están asociados con un servicio de lenguaje registrado. Sin embargo, no es necesario implementar un <xref:Microsoft.VisualStudio.Package.LanguageService> para registrar los fragmentos de código. En su lugar, simplemente especifique un GUID en el archivo de índice de fragmento de código y, a continuación, usar el mismo GUID en el <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> que agregue al proyecto.  
  
 Los pasos siguientes muestran cómo crear fragmentos de código y asociarlos con un GUID específico.  
  
1. Cree la siguiente estructura de directorios:  
  
    **%INSTALLDIR%\TestSnippets\Snippets\1033\\**  
  
    donde *% InstallDir %* es la carpeta de instalación de Visual Studio. (Aunque esta ruta de acceso se utiliza normalmente para instalar fragmentos de código, puede especificar cualquier ruta de acceso).  
  
2. En la carpeta \1033\, cree un *.xml* de archivo y asígnele el nombre **TestSnippets.xml**. (Aunque este nombre se utiliza normalmente para un archivo de índice de fragmento de código, puede especificar cualquier nombre siempre y cuando tenga un *.xml* la extensión de nombre de archivo.) Agregue el siguiente texto y, a continuación, eliminar el marcador de posición GUID y agregar los suyos propios.  
  
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
  
3. Cree un archivo en la carpeta de fragmento de código, asígnele el nombre **probar**`.snippet`y, a continuación, agregue el siguiente texto:  
  
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
  
### <a name="to-register-code-snippets-for-a-specific-guid"></a>Para registrar los fragmentos de código para un GUID específico  
  
1.  Abra el **CompletionTest** proyecto. Para obtener información sobre cómo crear este proyecto, vea [Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2.  En el proyecto, agregue referencias a los ensamblados siguientes:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   Microsoft.MSXML  
  
3.  En el proyecto, abra el **source.extension.vsixmanifest** archivo.  
  
4.  Asegúrese de que el **activos** pestaña contiene un **VsPackage** de contenido de tipo y que **proyecto** se establece en el nombre del proyecto.  
  
5.  Seleccione el proyecto CompletionTest y en la ventana Propiedades, establezca **generar archivo Pkgdef** a **true**. Guarde el proyecto.  
  
6.  Agregar una variable static `SnippetUtilities` clase al proyecto.  
  
     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]  
  
7.  En la clase SnippetUtilities, definir un GUID y asignarle el valor que utilizó en el *SnippetsIndex.xml* archivo.  
  
     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]  
  
8.  Agregar el <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> a la `TestCompletionHandler` clase. Este atributo puede agregarse a cualquier clase (no estáticos) de público o interno en el proyecto. (Es posible que deba agregar una `using` instrucción del espacio de nombres Microsoft.VisualStudio.Shell.)  
  
     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]  
  
9. Compile y ejecute el proyecto. En la instancia experimental de Visual Studio que se inicia cuando se ejecuta el proyecto, se debe mostrar el fragmento de código que acaba de registrar en el **Administrador de fragmentos de código** bajo el **TestSnippets** lenguaje.  
  
## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Agregue el comando Insertar fragmento de código en el menú contextual  
 El **Insertar fragmento de código** comando no se incluye en el menú contextual de un archivo de texto. Por lo tanto, debe habilitar el comando.  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Para agregar el comando Insertar fragmento de código en el menú contextual  
  
1.  Abra el `TestCompletionCommandHandler` archivo de clase.  
  
     Dado que esta clase implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, puede activar el **Insertar fragmento de código** comando en el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método. Antes de habilitar el comando, compruebe que este método no se llama dentro de una función de automatización porque cuando el **Insertar fragmento de código** se hace clic en el comando, se muestra la interfaz de usuario de selector de fragmento de código (UI).  
  
     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]  
  
2.  Compile y ejecute el proyecto. En la instancia experimental, abra un archivo que tiene el *.zzz* la extensión de nombre de archivo y, a continuación, haga doble clic en cualquier lugar en él. El **Insertar fragmento de código** comando debe aparecer en el menú contextual.  
  
## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Implementar la expansión del fragmento de código en la interfaz de usuario de selector de fragmento de código  
 En esta sección se muestra cómo implementar la expansión del fragmento de código para que sea el selector de fragmentos de la interfaz de usuario que se muestran cuando **Insertar fragmento de código** se hace clic en el menú contextual. Un fragmento de código también se expande cuando un usuario escribe el acceso directo del fragmento de código y, a continuación, presiona **ficha**.  
  
 Para mostrar el selector de fragmentos de la interfaz de usuario y para habilitar la navegación y la aceptación de fragmento de código posterior a la inserción, use el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método. La inserción en sí se controla mediante el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> método.  
  
 La implementación de expansión del fragmento de código usa heredado <xref:Microsoft.VisualStudio.TextManager.Interop> interfaces. Al traducir desde las clases de editor actual para el código heredado, recuerde que las interfaces heredadas usan una combinación de números de línea y columna para especificar las ubicaciones en un búfer de texto, pero las clases actuales usan un índice. Por lo tanto, si un búfer tiene tres líneas de cada uno de los cuales tiene 10 caracteres (más de una nueva línea, que se considera un carácter), el cuarto carácter en la tercera línea está en posición 27 en la implementación actual, pero resulta en la línea 2, posición 3 en la implementación anterior.  
  
#### <a name="to-implement-snippet-expansion"></a>Para implementar la expansión del fragmento de código  
  
1.  En el archivo que contiene el `TestCompletionCommandHandler` clase, agregue las siguientes `using` instrucciones.  
  
     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]  
  
2.  Realizar el `TestCompletionCommandHandler` clase implemente la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfaz.  
  
     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]  
  
3.  En el `TestCompletionCommandHandlerProvider` class, importar el <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.  
  
     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]  
  
4.  Agregue algunos campos privados para las interfaces de expansión de código y la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]  
  
5.  En el constructor de la `TestCompletionCommandHandler` clase, establezca los siguientes campos.  
  
     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]  
  
6.  Para mostrar el selector de fragmentos cuando el usuario hace clic en el **Insertar fragmento de código** de comandos, agregue el código siguiente a la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método. (Para que sea más legible, esta explicación el `Exec()`no se muestra el código que se usa para la finalización de instrucciones; en su lugar, se agregan los bloques de código al método existente.) Agregue el siguiente bloque de código después del código que busca un carácter.  
  
     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]  
  
7.  Si un fragmento de código tiene campos que se pueden navegar, la sesión de expansión se mantiene abierta hasta que explícitamente se acepta la expansión; Si el fragmento de código no tiene campos, la sesión se cierra y se devuelve como `null` por el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> método. En el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método, tras el selector de fragmentos de código de interfaz de usuario que agregó en el paso anterior, agregue el siguiente código para controlar la navegación del fragmento de código (cuando el usuario presiona **ficha** o **MAYÚS** + **Ficha** después de la inserción de fragmento de código).  
  
     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]  
  
8.  Para insertar el fragmento de código cuando el usuario escribe el método abreviado correspondiente y, a continuación, presiona **ficha**, agregue código a la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método. El método privado que inserta el fragmento de código se mostrará en un paso posterior. Agregue el código siguiente después del código de navegación que agregó en el paso anterior.  
  
     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]  
  
9. Implemente los métodos de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfaz. En esta implementación, los únicos métodos de interés son <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Los otros métodos deben devolver simplemente <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]  
  
10. Implemente el método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. El método auxiliar que se inserta realmente las expansiones se trata en un paso posterior. El <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> proporciona información de línea y columna, que se puede obtener desde el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]  
  
11. El método privado siguiente inserta un fragmento de código, basándose en el acceso directo o en el título y la ruta de acceso. A continuación, llama el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> método con el fragmento de código.  
  
     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]  
  
## <a name="build-and-test-code-snippet-expansion"></a>Compilar y probar la expansión del fragmento de código  
 Puede probar si funciona la expansión del fragmento de código en el proyecto.  
  
1.  Compile la solución. Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.  
  
2.  Abra un archivo de texto y escriba algún texto.  
  
3.  Haga clic en algún lugar en el texto y, a continuación, haga clic en **Insertar fragmento de código**.  
  
4.  El selector de fragmentos de la interfaz de usuario debe aparecer con un ventana emergente que dice **probar campos de reemplazo**. Haga doble clic en el menú emergente.  
  
     Se debe insertar el fragmento de código siguiente.  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     No presione **ENTRAR** o **Esc**.  
  
5.  Presione **ficha** y **MAYÚS**+**ficha** para alternar entre "first" y "segundo".  
  
6.  Acepte la inserción presionando **ENTRAR** o **Esc**.  
  
7.  En una parte distinta del texto, escriba "test" y, a continuación, presione **ficha**. Debido a "test" es el método abreviado de fragmento de código, se debe insertar el fragmento de código nuevo.  
  
## <a name="next-steps"></a>Pasos siguientes