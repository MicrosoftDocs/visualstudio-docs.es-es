---
title: 'Tutorial: Crear un fragmento de código'
ms.date: 06/10/2019
ms.topic: conceptual
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6f58581a601da59e7ff66a3bae5ddcb7432bf8e3
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836099"
---
# <a name="walkthrough-create-a-code-snippet"></a>Tutorial: Crear un fragmento de código

Puede crear un fragmento de código en unos pocos pasos. Lo único que debe hacer es crear un archivo XML, rellenar los elementos correspondientes y agregarle código. Opcionalmente, puede hacer uso de parámetros de reemplazo y referencias de proyecto. Importar el fragmento de código a la instalación de Visual Studio mediante el **importación** situado en la **Administrador de fragmentos de código** (**herramientas** > **código Administrador de fragmentos de**).

## <a name="snippet-template"></a>Plantilla de fragmento de código

El siguiente código XML es la plantilla de fragmento de código básico:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title></Title>
        </Header>
        <Snippet>
            <Code Language="">
                <![CDATA[]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="create-a-code-snippet"></a>Crear un fragmento de código

1. Cree un archivo XML en Visual Studio y agregue la plantilla que se ha mostrado anteriormente.

2. Rellene el título del fragmento de código en el **título** elemento. Utilice el título **raíz cuadrada**.

3. Rellene el lenguaje del fragmento de código en el atributo **Language** del elemento **Code**. Para C#, utilice **CSharp**y Visual Basic, utilice **VB**.

   > [!TIP]
   > Para ver todos los valores de idioma disponibles, vaya el [sección atributos del elemento de código](code-snippets-schema-reference.md#attributes) en el [referencia de esquema de fragmentos de código](code-snippets-schema-reference.md) página.

4. Agregar el fragmento de código en el **CDATA** sección dentro la **código** elemento.

   Para C#:

   ```xml
   <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt(16);]]>
   </Code>
   ```

   O para Visual Basic:

   ```xml
   <Code Language="VB">
       <![CDATA[Dim root = Math.Sqrt(16)]]>
   </Code>
   ```

5. Guarde el fragmento de código como *SquareRoot.snippet* (puede guardarla en cualquier lugar).

## <a name="import-a-code-snippet"></a>Importar un fragmento de código

1. Puede importar un fragmento de código a la instalación de Visual Studio mediante el **Administrador de fragmentos de código**. Ábralo eligiendo **herramientas** > **Administrador de fragmentos de código**.

2. Haga clic en el botón **Importar**.

3. Vaya a la ubicación donde ha guardado el fragmento de código en el procedimiento anterior, selecciónelo y haga clic en **Abrir**.

4. Se abre el cuadro de diálogo **Importar fragmento de código**, que le pide que elija entre las opciones del panel derecho dónde agregar el fragmento de código. Una de las opciones debería ser **Mis fragmentos de código**. Selecciónela, haga clic en **Finalizar** y después en **Aceptar**.

5. El fragmento de código se copia en una de las ubicaciones siguientes, dependiendo del lenguaje de código:

   ::: moniker range="vs-2017"

   *%USERPROFILE%\Documents\Visual studio 2017\Code Snippets\Visual C#fragmentos de código \My*
   *fragmentos de código %USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual Basic\My*

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   *%USERPROFILE%\Documents\Visual studio 2019\Code Snippets\Visual C#fragmentos de código \My*
   *fragmentos de código %USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual Basic\My*

   ::: moniker-end

6. Pruebe el fragmento abriendo un C# o proyecto de Visual Basic. Con un archivo de código abierto en el editor, elija **fragmentos** > **Insertar fragmento de código** desde el menú contextual, a continuación, **Mis fragmentos de código**. Debería ver un fragmento de código denominado **raíz cuadrada**. Haga doble clic en ella.

   El fragmento de código se inserta en el archivo de código.

## <a name="description-and-shortcut-fields"></a>Campos de descripción y el método abreviado

::: moniker range="vs-2017"

1. Los campos de descripción proporcionan más información sobre el fragmento de código cuando se visualiza en el Administrador de fragmentos de código. El acceso directo es una etiqueta que los usuarios pueden escribir con el fin de insertar el fragmento de código. Edite el fragmento de código que agregó abriendo el archivo *%USERPROFILE%\Documents\Visual Studio 2017\Code fragmentos\\[Visual C# o Visual Basic] \My Code Snippet\SquareRoot.snippet*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Los campos de descripción proporcionan más información sobre el fragmento de código cuando se visualiza en el Administrador de fragmentos de código. El acceso directo es una etiqueta que los usuarios pueden escribir con el fin de insertar el fragmento de código. Edite el fragmento de código que agregó abriendo el archivo *%USERPROFILE%\Documents\Visual Studio 2019\Code fragmentos\\[Visual C# o Visual Basic] \My Code Snippet\SquareRoot.snippet*.

::: moniker-end

   > [!TIP]
   > Puesto que está editando el archivo en el directorio donde Visual Studio colocado, no es necesario volver a importarlo a Visual Studio.

2. Agregue elementos **Author** y **Description** al elemento **Header** y rellénelos.

3. El elemento **Header** debe ser similar al siguiente:

   ```xml
   <Header>
       <Title>Square Root</Title>
       <Author>Myself</Author>
       <Description>Calculates the square root of 16.</Description>
   </Header>
   ```

4. Abra el **Administrador de fragmentos de código** y seleccione su fragmento de código. En el panel derecho, tenga en cuenta que el **descripción** y **autor** ahora se rellenan los campos.

   ![Descripción del fragmento de código en el Administrador de fragmentos de código](media/code-snippet-description-author.png)

5. Para agregar un acceso directo, agregue un **contextual** elemento dentro de la **encabezado** elemento:

   ```xml
   <Header>
      <Title>Square Root</Title>
      <Author>Myself</Author>
      <Description>Calculates the square root of 16.</Description>
      <Shortcut>sqrt</Shortcut>
    </Header>
   ```

6. Guarde de nuevo el archivo de fragmento de código.

7. Para probar el acceso directo, abra el proyecto usó anteriormente, escriba **sqrt** en el editor y presione **ficha** (una vez para Visual Basic, dos veces para C#).

   Se inserta el fragmento de código.

## <a name="replacement-parameters"></a>Parámetros de reemplazo

Desea que las partes de un fragmento de código sean reemplazadas por el usuario. Por ejemplo, es posible que desea que el usuario para reemplazar un nombre de variable con uno en su proyecto actual. Puede proporcionar dos tipos de reemplazos: literales y objetos. Use la [elemento Literal](code-snippets-schema-reference.md#literal-element) para identificar el reemplazo de un fragmento de código que está incluida completamente en el fragmento de código, pero probablemente tendrá que se personalice tras insertarla en el código (por ejemplo, un valor de cadena o numérica). Use la [elemento Object](code-snippets-schema-reference.md#object-element) para identificar un elemento que se requiere el fragmento de código, pero es probable que se defina fuera el fragmento de código por sí mismo (por ejemplo, una instancia de objeto o un control).

1. Para permitir al usuario reemplazar fácilmente el número para calcular la raíz cuadrada de, modifique la **fragmento** elemento de la *SquareRoot.snippet* archivo como sigue:

   ```xml
   <Snippet>
     <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt($Number$);]]>
     </Code>
     <Declarations>
       <Literal>
         <ID>Number</ID>
         <ToolTip>Choose the number you want the square root of.</ToolTip>
         <Default>16</Default>
       </Literal>
     </Declarations>
   </Snippet>
   ```

   Tenga en cuenta que el reemplazo de literal es un identificador dado (`Number`). Que identificador hace referencia desde dentro del fragmento de código que lo rodea con `$` caracteres:

   ```xml
   <![CDATA[double root = Math.Sqrt($Number$);]]>
   ```

2. Guarde el archivo de fragmento de código.

3. Abra un proyecto e insertar el fragmento de código.

   Se inserta el fragmento de código y se resalta el literal editable para el reemplazo. Mantenga el mouse sobre el parámetro de reemplazo para ver la información sobre herramientas para el valor.

   ![Código tooltip de parámetro de reemplazo de fragmento de código en Visual Studio](media/snippet-replacement-parameter-tooltip.png)

   > [!TIP]
   > Si hay más de un parámetro replacable en un fragmento de código, puede presionar **ficha** para navegar de uno a otro para cambiar los valores.

## <a name="import-a-namespace"></a>Importar un espacio de nombres

Puede usar un fragmento de código para agregar un `using` directiva (C#) o `Imports` (instrucción, Visual Basic) mediante la inclusión de la [elemento Imports](code-snippets-schema-reference.md#imports-element). Para los proyectos de .NET Framework, también puede agregar una referencia al proyecto mediante el [References (elemento)](code-snippets-schema-reference.md#references-element).

El siguiente XML muestra un fragmento de código que utiliza el método `File.Exists` en el espacio de nombres System.IO y, por lo tanto, define la **importaciones** elemento que se va a importar el espacio de nombres System.IO.

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>File Exists</Title>
      <Shortcut>exists</Shortcut>
    </Header>
    <Snippet>
      <Code Language="CSharp">
        <![CDATA[var exists = File.Exists("C:\\Temp\\Notes.txt");]]>
      </Code>
      <Imports>
        <Import>
          <Namespace>System.IO</Namespace>
        </Import>
      </Imports>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>Vea también

- [Referencia de esquemas de fragmentos de código](../ide/code-snippets-schema-reference.md)