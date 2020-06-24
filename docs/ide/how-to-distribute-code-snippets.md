---
title: Distribución de fragmentos de código como extensión
ms.date: 03/21/2019
ms.topic: how-to
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: c283d5ca29b67e772df2a0bb2e25dee70cd63fd3
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284378"
---
# <a name="how-to-distribute-code-snippets"></a>Procedimiento Distribuir fragmentos de código

Los fragmentos de código se pueden entregar a los compañeros para que los instalen en sus equipos mediante el **Administrador de fragmentos de código**. Aunque si tiene que distribuir varios fragmentos de código o quiere distribuirlos más ampliamente, puede incluir los archivos de fragmento de código en una extensión de Visual Studio. Los usuarios de Visual Studio pueden después instalar la extensión para obtener los fragmentos de código.

## <a name="prerequisites"></a>Requisitos previos

Instalar la carga de trabajo **Desarrollo de extensiones de Visual Studio** para obtener acceso a las plantillas de proyecto **Proyecto VSIX**.

![Carga de trabajo Desarrollo de extensiones de Visual Studio](media/vs-2019/extension-development-workload.png)

## <a name="set-up-the-extension"></a>Configurar la extensión

En este procedimiento se usa el mismo fragmento de código de Hola mundo creado en [Tutorial: Creación de un fragmento de código](../ide/walkthrough-creating-a-code-snippet.md). En este artículo se ofrece el fragmento de código de XML, por lo que no tendrá que volver atrás y crear un fragmento de código.

1. Cree un proyecto a partir de la plantilla **Proyecto VSIX vacío** y asígnele el nombre **TestSnippet**.

2. En el proyecto **TestSnippet**, agregue un nuevo archivo XML con el nombre *VBCodeSnippet.snippet*. Reemplace el contenido por el siguiente XML:

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

### <a name="set-up-the-directory-structure"></a>Configurar la estructura de directorios

1. En el **Explorador de soluciones**, seleccione el nodo del proyecto y agregue una carpeta que tenga el mismo nombre que quiere para el fragmento de código en el **Administrador de fragmentos de código**. En este caso sería **HelloWorldVB**.

2. Mueva el archivo *.snippet* a la carpeta *HelloWorldVB*.

3. Seleccione el archivo *.snippet* en el **Explorador de soluciones** y, en la ventana **Propiedades**, asegúrese de que **Acción de compilación** esté establecido en **Contenido**, de que **Copiar en el directorio de salida** esté establecido en **Copiar siempre** y de que **Incluir en VSIX** esté establecido en **true**.

### <a name="add-the-pkgdef-file"></a>Agregar el archivo .pkgdef

::: moniker range="vs-2017"

1. Agregue un archivo de texto a la carpeta *HelloWorldVB* y asígnele el nombre *HelloWorldVB.pkgdef*. Este archivo se usa para agregar determinadas claves al registro. En este caso, agrega una nueva subclave a la clave **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Languages\CodeExpansions\Basic**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Agregue un archivo de texto a la carpeta *HelloWorldVB* y asígnele el nombre *HelloWorldVB.pkgdef*. Este archivo se usa para agregar determinadas claves al registro. En este caso, agrega una nueva subclave a la clave **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Languages\CodeExpansions\Basic**.

::: moniker-end

2. Agregue las líneas siguientes al archivo.

    ```txt
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

    Si examina esta clave, puede ver cómo especificar diferentes lenguajes.

3. Seleccione el archivo *.pkgdef* en el **Explorador de soluciones** y, en la ventana **Propiedades**, asegúrese de que:

   - **Acción de compilación** se establece en **Contenido**
   - **Copiar en el directorio de salida** está establecido en **Copiar siempre**
   - **Incluir en VSIX** está establecido en **true**

4. Agregue el archivo *.pkgdef* como activo en el manifiesto de VSIX. En el archivo *source.extension.vsixmanifest*, vaya a la pestaña **Activos** y haga clic en **Nuevo**.

5. En el cuadro de diálogo **Agregar nuevo activo**, establezca **Tipo** en **Microsoft.VisualStudio.VsPackage**, **Source** en **Archivo en filesystem** y **Ruta de acceso** en **HelloWorldVB.pkgdef** (debe aparecer en la lista desplegable).

### <a name="test-the-snippet"></a>Probar el fragmento de código

1. Ahora hay que asegurarse de que el fragmento de código funciona en la instancia experimental de Visual Studio. La instancia experimental es una segunda copia de Visual Studio que es independiente de la que se emplea para escribir código. Permite trabajar en una extensión sin que el entorno de desarrollo se vea afectado.

2. Compile la solución y comience la depuración.

   Se muestra una segunda instancia de Visual Studio.

3. En la instancia experimental, vaya a **Herramientas** > **Administrador de fragmentos de código** y establezca el **Lenguaje** en **Basic**. Verá que *HelloWorldVB* es una de las carpetas y podrá expandirla para ver el fragmento de código *HelloWorldVB*.

4. Pruebe el fragmento de código. En la instancia experimental, abra un proyecto de Visual Basic y luego abra uno de los archivos de código. Coloque el cursor en algún lugar del código, haga clic con el botón derecho y, en el menú contextual, seleccione **Insertar fragmento de código**.

5. Verá que una de las carpetas es *HelloWorldVB*. Haga doble clic en ella. Se debería ver un elemento emergente **Insertar fragmento de código: HelloWorldVB >** con una lista desplegable **HelloWorldVB**. Haga clic en la lista desplegable de **HelloWorldVB**.

   Se agrega la siguiente línea al archivo de código:

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>Vea también

- [Fragmentos de código](../ide/code-snippets.md)
