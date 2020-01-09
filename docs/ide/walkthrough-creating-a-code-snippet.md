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
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: adb0415e926bba9a1809c77f0f35b43d78263f43
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597300"
---
# <a name="walkthrough-create-a-code-snippet"></a>Tutorial: Crear un fragmento de código

Puede crear un fragmento de código en unos pocos pasos. Lo único que debe hacer es crear un archivo XML, rellenar los elementos correspondientes y agregarle código. Opcionalmente, puede usar parámetros de reemplazo y referencias de proyecto. Importe el fragmento de código a la instalación de Visual Studio mediante el botón **Importar** del **Administrador de fragmentos de código** (**Herramientas** > **Administrador de fragmentos de código**).

## <a name="snippet-template"></a>Plantilla de fragmento de código

El siguiente XML es la plantilla básica de fragmento de código:

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

2. Rellene el título del fragmento de código en el elemento **Título**. Use el título **Raíz cuadrada**.

3. Rellene el lenguaje del fragmento de código en el atributo **Language** del elemento **Code**. En C#, use **CSharp** y, en Visual Basic, **VB**.

   > [!TIP]
   > Para ver todos los valores de lenguaje disponibles, vaya a la sección [Atributos del elemento Code](code-snippets-schema-reference.md#attributes) de la página [Referencia de esquemas de fragmentos de código](code-snippets-schema-reference.md).

4. Agregue el código del fragmento de código en la sección **CDATA**, dentro del elemento **Code**.

   Para C#:

   ```xml
   <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt(16);]]>
   </Code>
   ```

   O bien, en Visual Basic:

   ```xml
   <Code Language="VB">
       <![CDATA[Dim root = Math.Sqrt(16)]]>
   </Code>
   ```

   > [!NOTE]
   > No puede especificar cómo se debe aplicar sangría o formato a las líneas de código en la sección **CDATA** de un fragmento de código. Después de la inserción, el servicio de lenguaje aplica el formato automáticamente al código insertado.

5. Guarde el fragmento de código como *SquareRoot.snippet* (puede guardarlo en cualquier lugar).

## <a name="import-a-code-snippet"></a>Importar un fragmento de código

1. Puede importar un fragmento de código a la instalación de Visual Studio mediante el **Administrador de fragmentos de código**. Para abrirlo, seleccione **Herramientas** > **Administrador de fragmentos de código**.

2. Haga clic en el botón **Importar**.

3. Vaya a la ubicación donde ha guardado el fragmento de código en el procedimiento anterior, selecciónelo y haga clic en **Abrir**.

4. Se abre el cuadro de diálogo **Importar fragmento de código**, que le pide que elija entre las opciones del panel derecho dónde agregar el fragmento de código. Una de las opciones debería ser **Mis fragmentos de código**. Selecciónela, haga clic en **Finalizar** y después en **Aceptar**.

5. El fragmento de código se copia en una de las ubicaciones siguientes, según el lenguaje del código:

   ::: moniker range="vs-2017"

   *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual C#\My Code Snippets*
    *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual Basic\My Code Snippets*

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual C#\My Code Snippets*
    *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual Basic\My Code Snippets*

   ::: moniker-end

6. Pruebe el fragmento de código. Para ello, abra un proyecto de C# o Visual Basic. Con un archivo de código abierto en el editor, seleccione **Fragmentos de código** > **Insertar fragmento de código** en el menú contextual y luego **Mis fragmentos de código**. Debería ver un fragmento de código denominado **Raíz cuadrada**. Haga doble clic en ella.

   El fragmento de código se inserta en el archivo de código.

## <a name="description-and-shortcut-fields"></a>Campos de descripción y de acceso directo

::: moniker range="vs-2017"

1. Los campos de descripción proporcionan más información sobre el fragmento de código cuando se visualiza en el Administrador de fragmentos de código. El acceso directo es una etiqueta que los usuarios pueden escribir con el fin de insertar el fragmento de código. Edite el fragmento de código que ha agregado. Para ello, abra el archivo *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\\[Visual C# o Visual Basic]\My Code Snippet\SquareRoot.snippet*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Los campos de descripción proporcionan más información sobre el fragmento de código cuando se visualiza en el Administrador de fragmentos de código. El acceso directo es una etiqueta que los usuarios pueden escribir con el fin de insertar el fragmento de código. Edite el fragmento de código que ha agregado. Para ello, abra el archivo *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\\[Visual C# o Visual Basic]\My Code Snippet\SquareRoot.snippet*.

::: moniker-end

   > [!TIP]
   > Puesto que está editando el archivo en el directorio donde Visual Studio lo ha colocado, no tiene que volver a importarlo a Visual Studio.

2. Agregue elementos **Author** y **Description** al elemento **Header** y rellénelos.

3. El elemento **Header** debe ser similar al siguiente:

   ```xml
   <Header>
       <Title>Square Root</Title>
       <Author>Myself</Author>
       <Description>Calculates the square root of 16.</Description>
   </Header>
   ```

4. Abra el **Administrador de fragmentos de código** y seleccione su fragmento de código. En el panel derecho, observe que ahora los campos **Descripción** y **Autor** están rellenos.

   ![Descripción del fragmento de código en el Administrador de fragmentos de código](media/code-snippet-description-author.png)

5. Para agregar un acceso directo, agregue un elemento **Acceso directo** dentro del elemento **Encabezado**:

   ```xml
   <Header>
      <Title>Square Root</Title>
      <Author>Myself</Author>
      <Description>Calculates the square root of 16.</Description>
      <Shortcut>sqrt</Shortcut>
    </Header>
   ```

6. Guarde de nuevo el archivo de fragmento de código.

7. Para probar el acceso directo, abra el proyecto que ha usado anteriormente, escriba **sqrt** en el editor y presione **Tab** (una vez en Visual Basic, dos veces en C#).

   Se inserta el fragmento de código.

## <a name="replacement-parameters"></a>Parámetros de reemplazo

Es posible que quiera que partes de un fragmento de código sean reemplazadas por el usuario. Por ejemplo, puede querer que el usuario reemplace un nombre de variable por uno de su proyecto actual. Puede proporcionar dos tipos de reemplazos: literales y objetos. Use el [elemento Literal](code-snippets-schema-reference.md#literal-element) para identificar un reemplazo de un fragmento de código que está totalmente incluido en el fragmento, pero que posiblemente se personalice una vez insertado en el código (por ejemplo, una cadena o un valor numérico). Use el [elemento Object](code-snippets-schema-reference.md#object-element) para identificar un elemento que el fragmento de código necesita pero que probablemente se defina fuera del propio fragmento de código (por ejemplo, una instancia de objeto o un control).

1. Para permitir al usuario reemplazar fácilmente el número cuya raíz cuadrada se va a calcular, modifique el elemento **Snippet** del archivo *SquareRoot.snippet* de esta forma:

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

   Observe que al reemplazo de literal se le asigna un identificador (`Number`). Se hace referencia a ese identificador desde dentro del fragmento de código al rodearlo con caracteres `$`:

   ```xml
   <![CDATA[double root = Math.Sqrt($Number$);]]>
   ```

2. Guarde el archivo de fragmento de código.

3. Abra un proyecto e inserte el fragmento de código.

   El fragmento de código se inserta y el literal editable se resalta para su reemplazo. Mantenga el mouse sobre el parámetro de reemplazo para ver la información sobre herramientas del valor.

   ![Información sobre herramientas de parámetro de reemplazo de fragmento de código en Visual Studio](media/snippet-replacement-parameter-tooltip.png)

   > [!TIP]
   > Si hay más de un parámetro reemplazable en un fragmento de código, puede presionar **Tab** para ir de uno a otro a fin de cambiar los valores.

## <a name="import-a-namespace"></a>Importar un espacio de nombres

Puede usar un fragmento de código para agregar una directiva `using` (C#) o una instrucción `Imports` (Visual Basic) mediante la inclusión del [elemento Imports](code-snippets-schema-reference.md#imports-element). En los proyectos de .NET Framework, también puede agregar una referencia al proyecto mediante el [elemento References](code-snippets-schema-reference.md#references-element).

El siguiente XML muestra un fragmento de código que usa el método `File.Exists` en el espacio de nombres System.IO y, por lo tanto, define el elemento **Imports** para importar el espacio de nombres System.IO.

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
