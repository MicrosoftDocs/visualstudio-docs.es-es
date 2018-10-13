---
title: 'Tutorial: Crear un fragmento de código | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 038635db92d08837cc6519670053c9619ebe3c9b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49267753"
---
# <a name="walkthrough-creating-a-code-snippet"></a>Tutorial: Crear un fragmento de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede crear un fragmento de código en unos pocos pasos. Lo único que debe hacer es crear un archivo XML, rellenar los elementos correspondientes y agregarle código. También puede agregar referencias y parámetros de reemplazo en el código. Puede agregar el fragmento de código a la instalación de Visual Studio con el botón de importación en el Administrador de fragmentos de código (**Administrador de fragmentos de código o herramientas**).  
  
> [!TIP]
>  Para obtener información sobre cómo escribir fragmentos de código más fácilmente, busque el sitio Web de CodePlex para herramientas de la Comunidad, como [Snippet Editor](http://go.microsoft.com/fwlink/?LinkId=251033).  
  
## <a name="snippet-template"></a>Plantilla de fragmento de código  
 Esta es la plantilla básica de fragmento de código:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CodeSnippets  
    xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
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
  
### <a name="to-create-a-code-snippet"></a>Para crear un fragmento de código  
  
1.  Cree un archivo XML en Visual Studio y agregue la plantilla que se ha mostrado anteriormente.  
  
2.  Rellene el título del fragmento de código, por ejemplo, "Hola mundo VB", en el elemento Title.  
  
3.  Rellene el lenguaje del fragmento de código en el atributo Languages del elemento Code. En este ejemplo, use "VB".  
  
4.  Agregue código en la sección CDATA dentro del elemento Code, por ejemplo:  
  
    ```  
    <Code Language="VB">  
        <![CDATA[Console.WriteLine("Hello, World!")]]>  
    </Code>  
  
    ```  
  
5.  Guarde el fragmento de código como VBCodeSnippet.snippet.  
  
### <a name="to-add-a-code-snippet-to-visual-studio"></a>Para agregar un fragmento de código a Visual Studio  
  
1.  Puede agregar sus propios fragmentos de código a la instalación de Visual Studio mediante el Administrador de fragmentos de código. Abra el Administrador de fragmentos de código (**Administrador de fragmentos de código o herramientas**).  
  
2.  Haga clic en el botón **Importar**.  
  
3.  Vaya a la ubicación donde ha guardado el fragmento de código en el procedimiento anterior, selecciónelo y haga clic en **Abrir**.  
  
4.  Se abre el cuadro de diálogo **Importar fragmento de código**, que le pide que elija entre las opciones del panel derecho dónde agregar el fragmento de código. Una de las opciones debería ser **Mis fragmentos de código**. Selecciónela, haga clic en **Finalizar** y después en **Aceptar**.  
  
5.  El fragmento de código se copia en la ubicación siguiente:  
  
     `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippets`  
  
6.  Pruebe el fragmento de código. Para ello, abra un proyecto de Visual Basic y abra un archivo de código. En el archivo, haga clic en **Insertar fragmento de código** en el menú contextual y elija **Mis fragmentos de código**. Debería ver un fragmento de código denominado **My Visual Basic Code Snippet** (Mi fragmento de código de Visual Basic). Haga doble clic en ella.  
  
7.  Debería ver `Console.WriteLine("Hello, World!")` insertado en el código.  
  
### <a name="adding-description-and-shortcut-fields"></a>Agregar campos de descripción y de acceso directo  
  
1.  Los campos de descripción proporcionan más información sobre el fragmento de código cuando se visualiza en el Administrador de fragmentos de código. El acceso directo es una etiqueta que los usuarios pueden escribir con el fin de insertar el fragmento de código. Edite el fragmento de código que agregó abriendo el archivo `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet`.  
  
2.  Agregue elementos Author y Description al elemento Header y rellénelos.  
  
3.  El elemento Header debe ser similar al siguiente:  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
    </Header>  
  
    ```  
  
4.  Abra el Administrador de fragmentos de código y seleccione su fragmento de código. En el panel derecho verá que ahora los campos Description y Author están rellenados.  
  
5.  Para agregar un acceso directo, agregue un elemento Shortcut junto a los elementos Author y Description:  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
        <Shortcut>hello</Shortcut>  
    </Header>  
  
    ```  
  
6.  Guarde de nuevo el archivo de fragmento de código.  
  
7.  Para probar el acceso directo, abra un proyecto de Visual Basic y abra un archivo de código. Tipo `hello` en el archivo y presione TAB. Se debe insertar el fragmento de código.  
  
### <a name="to-add-references-and-imports"></a>Para agregar referencias e importaciones  
  
1.  Con fragmentos de código de Visual Basic, puede agregar una referencia a un proyecto mediante el elemento References y agregar una declaración de importaciones mediante el elemento Imports. (Los fragmentos de código en otros lenguajes no tienen esta característica). Por ejemplo, si cambia `Console.WriteLine` a `MessageBox.Show` en el ejemplo de código, puede que necesite agregar el ensamblado System.Windows.Forms.dll al proyecto.  
  
2.  Abra el fragmento de código.  
  
3.  Agregue el elemento References bajo el elemento Snippet:  
  
    ```  
    <References>  
        <Reference>  
            <Assembly>System.Windows.Forms.dll</Assembly>  
        </Reference>  
    </References>  
  
    ```  
  
4.  Agregue el elemento Imports bajo el elemento Snippet:  
  
    ```  
    <Imports>  
        <Import>  
           <Namespace>System.Windows.Forms</Namespace>  
        </Import>  
    </Imports>  
  
    ```  
  
5.  Cambie la sección CDATA a lo siguiente:  
  
    ```  
    <![CDATA[MessageBox.Show("Hello, World!")]]>  
    ```  
  
6.  Guarde el fragmento de código.  
  
7.  Abra un proyecto de Visual Basic y agregue el fragmento de código.  
  
8.  Verá una instrucción Imports en la parte superior del archivo de código:  
  
    ```  
    Imports System.Windows.Forms  
  
    ```  
  
9. Consulte las propiedades del proyecto. En la pestaña Referencias se incluye una referencia a System.Windows.Forms.dll.  
  
### <a name="adding-replacements"></a>Agregar reemplazos  
  
1.  Puede que le interese que el usuario reemplace algunas partes de los fragmentos de código, por ejemplo, si agrega una variable y quiere que el usuario la reemplace por una variable del proyecto actual. Puede proporcionar dos tipos de reemplazos: literales y objetos. Los literales son cadenas de cierto tipo (literales de cadena, nombres de variable o representaciones de cadena de valores numéricos). Los objetos son instancias de un tipo distinto de una cadena. En este procedimiento declarará un reemplazo de literal y un reemplazo de objeto y cambiará el código para que haga referencia a estos reemplazos.  
  
2.  Abra el fragmento de código.  
  
3.  En este ejemplo se usa una cadena de conexión SQL, por lo que debe cambiar los elementos Imports y References para agregar las referencias adecuadas:  
  
    ```  
    <References>  
        <Reference>  
            <Assembly>System.Data.dll</Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>System.Xml.dll</Assembly>  
        </Reference>  
    </References>  
    <Imports>  
        <Import>  
            <Namespace>System.Data</Namespace>  
        </Import>  
        <Import>  
            <Namespace>System.Data.SqlClient</Namespace>  
        </Import>  
    </Imports>  
  
    ```  
  
4.  Para declarar un reemplazo de literal para la cadena de conexión SQL, agregue un elemento Declarations bajo el elemento Snippet y agregue en él un elemento Literal con subelementos para el identificador, la información sobre herramientas y el valor predeterminado del reemplazo:  
  
    ```  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
    </Declarations>  
  
    ```  
  
5.  Para declarar un reemplazo de objeto para la conexión SQL, agregue un elemento Object dentro del elemento Declarations y agregue subelementos para el identificador, el tipo del objeto, la información sobre herramientas y el valor predeterminado. El elemento Declarations resultante debe ser similar al siguiente:  
  
    ```  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
        <Object>  
            <ID>SqlConnection</ID>  
            <Type>System.Data.SqlClient.SqlConnection</Type>  
            <ToolTip>Replace with a connection object in your application.</ToolTip>  
            <Default>dcConnection</Default>  
        </Object>  
    </Declarations>  
    ```  
  
6.  En la sección de código, las referencias a los reemplazos se rodean con signos $, por ejemplo, `$replacement$`:  
  
    ```  
    <Code Language="VB" Kind="method body">  
        <![CDATA[Dim daCustomers As SqlDataAdapter  
            Dim selectCommand As SqlCommand  
  
            daCustomers = New SqlClient.SqlDataAdapter()  
            selectCommand = new SqlClient.SqlCommand($SqlConnString$)  
            daCustomers.SelectCommand = selectCommand  
            daCustomers.SelectCommand.Connection = $SqlConnection$]]>  
    </Code>  
    ```  
  
7.  Guarde el fragmento de código.  
  
8.  Abra un proyecto de Visual Basic y agregue el fragmento de código.  
  
9. El código debe ser similar al siguiente, donde los reemplazos `SQL connection string` y `dcConnection` se resaltan en color naranja claro. Presione la tecla TAB para desplazarse de uno a otro.  
  
    ```  
    Dim daCustomers As SqlDataAdapter  
    Dim selectCommand As SqlCommand  
  
    daCustomers = New SqlClient.SqlDataAdapter()  
    selectCommand = New SqlClient.SqlCommand("SQL connection string")  
    daCustomers.SelectCommand = selectCommand  
    daCustomers.SelectCommand.Connection = dcConnection  
  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquemas de fragmentos de código](../ide/code-snippets-schema-reference.md)



