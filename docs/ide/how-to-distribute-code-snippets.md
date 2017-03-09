---
title: "C&#243;mo: Distribuir fragmentos de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fragmentos de código, distribuir"
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Distribuir fragmentos de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los fragmentos de código se pueden entregar directamente a los compañeros para que los instalen en sus equipos mediante el Administrador de fragmentos de código.  No obstante, si tiene que distribuir varios fragmentos de código o le gustaría distribuirlos más ampliamente, incluya el archivo de fragmento de código en una extensión de Visual Studio que puedan instalar los usuarios de esta solución.  
  
 Debe instalar el SDK de Visual Studio para poder crear extensiones de Visual Studio.  Busque la versión del VSSDK que coincida con su instalación de Visual Studio en la página de [descargas de Visual Studio 2015](http://www.visualstudio.com/downloads/visual-studio-2015-downloads-vs.aspx).  
  
## Configura la extensión  
 En este procedimiento se usará el mismo fragmento de código de Hello World creado en el [Tutorial: Crear un fragmento de código](../ide/walkthrough-creating-a-code-snippet.md).  Nosotros le proporcionaremos el texto .snippet para que no tenga que volver a crearlo.  
  
1.  Cree un nuevo proyecto VSIX denominado TestSnippet.  \(**Archivo \/ Nuevo \/ Proyecto \/ Visual C\# \(o Visual Basic \/ Extensibilidad**\)  
  
2.  En el proyecto **TestSnippet**, agregue un nuevo archivo XML y llámelo VBCodeSnippet.snippet.  Reemplace el contenido por lo siguiente:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <CodeSnippets  
        xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
      <CodeSnippet Format="1.0.0">  
        <Header>  
          <Title>Hello World VB</Title>  
          <Shortcut>HelloWorld</Shortcut>  
          <Description>Inserts code</Description>  
          <Author>MSIT</Author>  
          <SnippetTypes>  
            <SnippetType>Expansion</SnippetType>  
            <SnippetType>SurroundsWith</SnippetType>  
          </SnippetTypes>  
        </Header>  
        <Snippet>  
          <Code Language="VB">  
            <![CDATA[Console.WriteLine("Hello, World!")]]>  
          </Code>  
        </Snippet>  
      </CodeSnippet>  
    </CodeSnippets>  
    ```  
  
#### Configurar la estructura de directorios  
  
1.  En el Explorador de soluciones, seleccione el nodo del proyecto y agregue una carpeta que tenga el mismo nombre que desea para el fragmento de código en el Administrador de fragmentos de código.  En este caso sería **HelloWorldVB**.  
  
2.  Mover el archivo .snippet a la carpeta **HelloWorldVB**.  
  
3.  Seleccione el archivo .snippet en el Explorador de soluciones y, en la ventana **Propiedades**, asegúrese de que **Acción de compilación** está establecido en **Contenido**, **Copiar en el directorio de salida** está establecido en **Copiar siempre** e **Incluir en VSIX** está establecido en **true**.  
  
#### Agregar el archivo .pkgdef  
  
1.  Agregue un archivo de texto a la carpeta **HelloWorldVB** y asígnele el nombre HelloWorldVB.pkgdef.  Este archivo se usa para agregar determinadas claves al registro.  En este caso se agrega una nueva clave a  
  
     HKCU\\Software\\Microsoft\\VisualStudio\\14.0\\Languages\\CodeExpansions\\Basic.  
  
2.  Agregue las líneas siguientes al archivo.  
  
    ```  
    // Visual Basic   
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]   
    "HelloWorldVB"="$PackageFolder$"  
    ```  
  
     Si examina esta clave, puede ver cómo especificar diferentes lenguajes.  
  
3.  Seleccione el archivo .snippet en el Explorador de soluciones y, en la ventana **Propiedades**, asegúrese de que **Acción de compilación** está establecido en **Contenido**, **Copiar en el directorio de salida** está establecido en **Copiar siempre** e **Incluir en VSIX** está establecido en **true**.  
  
4.  Agregue el archivo .pkgdef como activo en el manifiesto de VSIX.  En el archivo source.extension.vsixmanifest, vaya a la pestaña **Activos** y haga clic en **Nuevo**.  
  
5.  En el diálogo **Agregar nuevo activo**, establezca el **Tipo** en **Microsoft.VisualStudio.VsPackage**, el **Tipo** en **Archivo en filesystem** y la **Ruta de acceso** en **HelloWorldVB.pkgdef** \(esta opción debe aparecer en la lista desplegable\).  
  
### Probar el fragmento de código  
  
1.  Ahora hay que asegurarse de que el fragmento de código funciona en la instancia experimental de Visual Studio.  La instancia experimental es una segunda copia de Visual Studio que es independiente de la que se emplea para escribir código.  Permite trabajar en una extensión sin que el entorno de desarrollo se vea afectado.  
  
2.  Compile la solución y comience la depuración.  Aparece una segunda instancia de Visual Studio.  
  
3.  En la instancia experimental, vaya a **Herramientas \/ Administrador de fragmentos de código**  y establezca el **Lenguaje** a **Basic**.  Verá que HelloWorldVB es una de las carpetas y podrá expandirla para ver el fragmento de código HelloWorldVB.  
  
4.  Pruebe el fragmento de código.  En la instancia experimental, abra un proyecto de Visual Basic y luego abra uno de los archivos de código.  Coloque el cursor en algún lugar del código, haga clic con el botón secundario y en el menú contextual seleccione **Insertar fragmento de código**.  
  
5.  Verá que una de las carpetas es HelloWorldVB.  Haga doble clic en ella.  Verá un elemento emergente **Insertar fragmento de código: HelloWorldVB \>** con una lista desplegable **HelloWorldVB**.  Haga clic en la lista desplegable de HelloWorldVB.  Verá la línea siguiente agregada al archivo:  
  
    ```vb  
    Console.WriteLine("Hello, World!")  
    ```  
  
## Vea también  
 [Fragmentos de código](../ide/code-snippets.md)