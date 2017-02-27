---
title: "Tutorial: Implementar fragmentos de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Tutorial: Implementar fragmentos de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede crear fragmentos de código e incluirlos en una extensión del editor para que los usuarios de la extensión pueden agregarlas a su propio código.  
  
 Un fragmento de código es un fragmento de código o cualquier otro texto que se puede incorporar en un archivo. Para ver todos los fragmentos de código que se han registrado para lenguajes de programación concretos en el **herramientas** menú, haga clic en **Administrador de fragmentos de código**. Para insertar un fragmento de código en un archivo, con el botón secundario donde desee que el fragmento de código, haga clic en **Insertar fragmento de código** o **Rodear con**, localice el fragmento de código que desee y, a continuación, haga doble clic en él. Presione TAB o MAYÚS\+TAB para modificar las partes relevantes del fragmento de código y, a continuación, presione ENTRAR o ESC para aceptarlo. Para obtener más información, consulta [Fragmentos de código](../ide/code-snippets.md).  
  
 Un fragmento de código se encuentra en un archivo XML que tiene la extensión de nombre de archivo .snippet. Un fragmento de código puede contener campos que se resaltan después de inserta el fragmento de código para que el usuario pueda buscar y cambiarlos. Un archivo de fragmento de código también proporciona información para la **Administrador de fragmentos de código** para que pueda mostrar el nombre del fragmento de código en la categoría correcta. Para obtener información acerca del esquema del fragmento de código, consulte [Referencia de esquemas de fragmentos de código](../ide/code-snippets-schema-reference.md).  
  
 Este tutorial enseña cómo realizar estas tareas:  
  
1.  Cree y registre los fragmentos de código para un idioma específico.  
  
2.  Agregue el **Insertar fragmento de código** comando a un menú contextual.  
  
3.  Implementar la expansión de fragmento de código.  
  
 En este tutorial se basa en [Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md).  
  
## Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulta [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Creación y registro de fragmentos de código  
 Normalmente, fragmentos de código están asociados a un servicio de lenguaje registrado. Sin embargo, no es necesario implementar un <xref:Microsoft.VisualStudio.Package.LanguageService> para registrar los fragmentos de código. En su lugar, simplemente especifique un GUID en el archivo de índice de fragmento de código y, a continuación, utilizar el mismo GUID en el <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> que agregue al proyecto.  
  
 Los pasos siguientes muestran cómo crear fragmentos de código y asociarlos con un GUID específico.  
  
1.  Cree la siguiente estructura de directorios:  
  
     **%INSTALLDIR%\\TestSnippets\\Snippets\\1033\\**  
  
     donde *% InstallDir %* es la carpeta de instalación de Visual Studio. \(Aunque esta ruta de acceso se utiliza normalmente para instalar fragmentos de código, puede especificar cualquier ruta de acceso\).  
  
2.  En la carpeta \\1033\\, cree un archivo .xml y asígnele el nombre **TestSnippets.xml**. \(Aunque este nombre se utiliza normalmente para un archivo de índice de fragmento de código, puede especificar cualquier nombre siempre y cuando tenga una extensión de nombre de archivo .xml.\) Agregue el siguiente texto y, a continuación, eliminar el marcador de posición GUID y agregar los suyos propios.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?> <SnippetCollection> <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}"> <SnippetDir> <OnOff>On</OnOff> <Installed>true</Installed> <Locale>1033</Locale> <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath> <LocalizedName>Snippets</LocalizedName> </SnippetDir> </Language> </SnippetCollection>  
    ```  
  
3.  Crear un archivo en la carpeta de fragmento de código, asígnele el nombre **probar**`.snippet`, y, a continuación, agregue el siguiente texto:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?> <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet"> <CodeSnippet Format="1.0.0"> <Header> <Title>Test replacement fields</Title> <Shortcut>test</Shortcut> <Description>Code snippet for testing replacement fields</Description> <Author>MSIT</Author> <SnippetTypes> <SnippetType>Expansion</SnippetType> </SnippetTypes> </Header> <Snippet> <Declarations> <Literal> <ID>param1</ID> <ToolTip>First field</ToolTip> <Default>first</Default> </Literal> <Literal> <ID>param2</ID> <ToolTip>Second field</ToolTip> <Default>second</Default> </Literal> </Declarations> <References> <Reference> <Assembly>System.Windows.Forms.dll</Assembly> </Reference> </References> <Code Language="TestSnippets"> <![CDATA[MessageBox.Show("$param1$"); MessageBox.Show("$param2$");]]> </Code> </Snippet> </CodeSnippet> </CodeSnippets>  
    ```  
  
 Los pasos siguientes muestran cómo registrar los fragmentos de código.  
  
#### Para registrar los fragmentos de código para un GUID específico  
  
1.  Abra la **CompletionTest** proyecto. Para obtener información sobre cómo crear este proyecto, consulte [Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2.  En el proyecto, agregue referencias a los ensamblados siguientes:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   Microsoft.MSXML  
  
3.  En el proyecto, abra el archivo source.extension.vsixmanifest.  
  
4.  Asegúrese de que el **activos** ficha contiene un **VsPackage** contenido tipo y que **proyecto** se establece en el nombre del proyecto.  
  
5.  Seleccione el proyecto CompletionTest y en la ventana Propiedades, establezca **Generar archivo de Pkgdef** a **true**. Guarde el proyecto.  
  
6.  Agregue una variable static `SnippetUtilities` clase al proyecto.  
  
     [!code-cs[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]  
  
7.  En la clase SnippetUtilities, definir un GUID y asígnele el valor que utiliza en el archivo SnippetsIndex.xml.  
  
     [!code-cs[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]  
  
8.  Agregue el <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> a la `TestCompletionHandler` clase. Este atributo se puede agregar a cualquier clase de \(no estáticos\) pública o interna en el proyecto. \(Es posible que deba agregar una `using` instrucción del espacio de nombres Microsoft.VisualStudio.Shell.\)  
  
     [!code-cs[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]  
  
9. Compile y ejecute el proyecto. En la instancia experimental de Visual Studio que se inicia cuando se ejecuta el proyecto, debe mostrarse el fragmento de código que acaba de registrar en el **Administrador de fragmentos de código** en el **TestSnippets** language.  
  
## Agregar el comando de Insertar fragmento de código en el menú contextual  
 El **Insertar fragmento de código** comando no se incluye en el menú contextual de un archivo de texto. Por lo tanto, debe habilitar el comando.  
  
#### Para agregar el comando Insertar fragmento de código en el menú contextual  
  
1.  Abra la `TestCompletionCommandHandler` archivo de clase.  
  
     Dado que esta clase implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, puede activar la **Insertar fragmento de código** comando el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método. Antes de habilitar el comando, compruebe que no se llama a este método dentro de una función de automatización porque cuando el **Insertar fragmento de código** se hace clic en el comando, se mostrará la interfaz de usuario de selector de fragmento de código \(UI\).  
  
     [!code-cs[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]  
  
2.  Compile y ejecute el proyecto. En la instancia experimental, abra un archivo que tiene la extensión de nombre de archivo .zzz y ratón en él. El **Insertar fragmento de código** comando debe aparecer en el menú contextual.  
  
## Implementación de expansión de fragmento de código en el selector de fragmentos de UI  
 Esta sección muestra cómo implementar la expansión de fragmento de código para que sea el selector de fragmentos de UI que se muestra cuando **Insertar fragmento de código** se hace clic en el menú contextual. Un fragmento de código también se expande cuando un usuario escribe el acceso directo del fragmento de código y, a continuación, presiona TAB.  
  
 Para mostrar el selector de fragmentos de UI y para habilitar la exploración y la aceptación de fragmento de código después de la inserción, use la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método. La inserción en sí se controla mediante el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> método.  
  
 La implementación de expansión de fragmento de código utiliza heredado <xref:Microsoft.VisualStudio.TextManager.Interop> interfaces. Al convertir de las clases de editor actual para el código heredado, recuerde que las interfaces heredadas usan una combinación de números de línea y columna para especificar ubicaciones en un búfer de texto, pero las clases actuales usan un índice. Por lo tanto, si un búfer tiene tres líneas de cada uno de los cuales tiene diez caracteres \(además de una nueva línea, que cuenta como 1 carácter\), el cuarto carácter en la tercera línea está en posición 27 en la implementación actual, pero está en la línea 2, posición 3 en la implementación anterior.  
  
#### Para implementar la expansión de fragmento de código  
  
1.  El archivo que contiene el `TestCompletionCommandHandler` agregue la siguiente `using` instrucciones.  
  
     [!code-cs[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]  
  
2.  Realizar la `TestCompletionCommandHandler` clase implemente la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfaz.  
  
     [!code-cs[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]  
  
3.  En la `TestCompletionCommandHandlerProvider` clase, importe la <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.  
  
     [!code-cs[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]  
  
4.  Agregue algunos campos privados para las interfaces de expansión de código y la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-cs[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]  
  
5.  En el constructor de la `TestCompletionCommandHandler` clase, establezca los siguientes campos.  
  
     [!code-cs[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]  
  
6.  Para mostrar el selector de fragmentos cuando el usuario hace clic en el **Insertar fragmento de código** de comandos, agregue el código siguiente a la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> \(método\). \(Para que esta explicación sea más legible, no se muestra el código Exec\(\) que se usa para completar la instrucción; en su lugar, se agregan los bloques de código al método existente\). Agregue el siguiente bloque de código después del código que busca un carácter.  
  
     [!code-cs[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]  
  
7.  Si un fragmento de código tiene campos que pueden navegar, la sesión de expansión se mantiene abierta hasta que explícitamente se acepta la expansión; Si el fragmento de código no tiene campos, la sesión se cierra y se devuelve como `null` por el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> \(método\). En la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> \(método\), tras el selector de fragmentos de código de interfaz de usuario que agregó en el paso anterior, agregue el siguiente código para controlar la navegación de fragmento de código \(cuando el usuario presiona TAB o MAYÚS\+TAB después de la inserción de fragmento de código\).  
  
     [!code-cs[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]  
  
8.  Para insertar el fragmento de código cuando el usuario escribe el acceso directo correspondiente y, a continuación, presiona TAB, agregue código a la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> \(método\). El método privado que inserta el fragmento de código se mostrará en un paso posterior. Agregue el código siguiente después del código de navegación que agregó en el paso anterior.  
  
     [!code-cs[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]  
  
9. Implemente los métodos de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfaz. En esta implementación, los únicos métodos de interés son <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Los demás métodos sólo deben devolver <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
     [!code-cs[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]  
  
10. Implemente el método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. El método auxiliar que se inserta realmente las expansiones se tratarán en un paso posterior. El <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> proporciona información de línea y columna, que puede obtener en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-cs[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]  
  
11. El método privado siguiente inserta un fragmento de código, basándose en el acceso directo o en el título y la ruta de acceso. A continuación, llama el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> método con el fragmento de código.  
  
     [!code-cs[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]  
  
## Compilar y probar la expansión de fragmento de código  
 Puede probar si la expansión de fragmento de código funciona en el proyecto.  
  
1.  Compile la solución. Cuando se ejecuta este proyecto en el depurador, se crea una instancia de una segunda instancia de Visual Studio.  
  
2.  Abra un archivo de texto y escriba algún texto.  
  
3.  Haga clic derecho en el texto y, a continuación, haga clic en **Insertar fragmento de código**.  
  
4.  El selector de fragmentos de IU debe aparecer con un mensaje emergente que dice **campos de reemplazo de prueba**. Haga doble clic en el menú emergente.  
  
     Se debe insertar el fragmento de código siguiente.  
  
    ```  
    MessageBox.Show("first"); MessageBox.Show("second");  
    ```  
  
     No presione ENTRAR o ESC.  
  
5.  Presionar TAB y MAYÚS\+TAB para alternar entre "first" y "segundo".  
  
6.  Acepte la inserción presionando ENTRAR o ESC.  
  
7.  En una parte distinta del texto, escriba "prueba" y, a continuación, presione la tecla TAB. Como "prueba" es el acceso directo del fragmento de código, se debe insertar el fragmento de código nuevo.  
  
## Pasos siguientes