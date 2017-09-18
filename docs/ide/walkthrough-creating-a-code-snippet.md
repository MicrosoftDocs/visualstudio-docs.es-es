---
title: "Tutorial: Crear un fragmento de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fragmentos de código, crear"
  - "fragmentos de código, importaciones"
  - "fragmentos de código, referencias"
  - "fragmentos de código, reemplazos"
  - "fragmentos de código, acceso directo"
  - "fragmentos de código, plantilla"
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Tutorial: Crear un fragmento de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede crear un fragmento de código con solo unos pasos.  Todo lo que tiene que hacer es crear un archivo XML, rellenar los elementos correspondientes y agregar su código.  También puede agregar referencias y parámetros de reemplazo a su código.  Puede agregar el fragmento de código a la instalación de Visual Studio mediante el botón de importación en el Administrador de fragmentos de código \(**Herramientas\/Administrador de fragmentos de código**\).  
  
> [!TIP]
>  Para obtener información sobre cómo escribir fragmentos de código más fácilmente, busque en el sitio web de CodePlex herramientas de la comunidad como, por ejemplo, el [Editor de fragmentos de código](http://go.microsoft.com/fwlink/?LinkId=251033).  
  
## Plantilla de fragmentos de código  
 La siguiente es la plantilla de fragmento de código básica:  
  
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
  
### Para crear un fragmento de código  
  
1.  Cree un nuevo archivo XML en Visual Studio y agregue la plantilla que se muestra anteriormente.  
  
2.  Rellene el título del fragmento de código como, por ejemplo, "Hello World VB" en el elemento de título.  
  
3.  Rellene el lenguaje del fragmento de código en el atributo Lenguajes del elemento Código.  Para este ejemplo, se usa "VB".  
  
4.  Agregue código de la sección CDATA al elemento de código, por ejemplo:  
  
    ```  
    <Code Language="VB">  
        <![CDATA[Console.WriteLine("Hello, World!")]]>  
    </Code>  
  
    ```  
  
5.  Guarde el fragmento como VBCodeSnippet.snippet.  
  
### Para agregar un fragmento de código a Visual Studio  
  
1.  Puede agregar sus propios fragmentos de código a la instalación de Visual Studio mediante el Administrador de fragmentos de código.  Abra el Administrador de fragmentos de código \(**Herramientas\/Administrador de fragmentos de código**\).  
  
2.  Haga clic en el botón **Importar**.  
  
3.  Vaya a la ubicación donde guardó el fragmento de código en el procedimiento anterior, selecciónelo y haga clic en **Abrir**.  
  
4.  El diálogo **Importar fragmento de código** se abre y le pide elegir dónde agregar el fragmento de código de las opciones del panel derecho.  Una de las opciones debe ser **Mis fragmentos de código**.  Seleccione y haga clic en **Finalizar** y, a continuación, haga clic en **Aceptar**.  
  
5.  El fragmento de código se copia en la siguiente ubicación:  
  
     `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippets`  
  
6.  Pruebe el fragmento. Para ello, abra un proyecto de Visual Basic y un archivo de código.  En el archivo, haga clic en **Insertar fragmento de código** del menú contextual y elija **Mis fragmentos de código**.  Debería ver un fragmento de código denominado **Mi fragmento de código de Visual Basic**.  Haga doble clic.  
  
7.  Debe ver `Console.WriteLine("Hello, World!")` insertado en el código.  
  
### Adición de campos de descripción y acceso directo  
  
1.  Los campos de descripción proporcionan más información acerca del fragmento de código cuando se visualiza en el Administrador de fragmentos de código.  El acceso directo es una etiqueta que los usuarios pueden escribir para insertar el fragmento.  Edite el fragmento de código que agregó abriendo el archivo `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet`.  
  
2.  Agregue los elementos Autor y Descripción al elemento Encabezado y complételos.  
  
3.  El elemento de encabezado debería tener el siguiente aspecto:  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
    </Header>  
  
    ```  
  
4.  Abra el Administrador de fragmentos de código y seleccione el fragmento de código.  En el panel derecho, debería ver que los campos Descripción y Autor están ahora rellenados.  
  
5.  Para agregar un acceso directo, agregue un elemento de acceso directo junto al elemento de Autor y Descripción:  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
        <Shortcut>hello</Shortcut>  
    </Header>  
  
    ```  
  
6.  Guarde el archivo de fragmento de nuevo.  
  
7.  Para probar el acceso directo, abra un proyecto de Visual Basic y abra un archivo de código.  Escriba `hello` en el archivo y presione la tecla TAB.  Se debe insertar el código del fragmento de código.  
  
### Para agregar importaciones y referencias  
  
1.  Con fragmentos de Visual Basic puede agregar una referencia a un proyecto mediante el elemento Referencias y agregar una declaración de importaciones mediante el elemento Imports. \(Los fragmentos de código de otros idiomas no disponen de esta característica.\) Por ejemplo, si cambia `Console.WriteLine` en el ejemplo de código a `MessageBox.Show`, puede que necesite agregar el ensamblado System.Windows.Forms.dll al proyecto.  
  
2.  Abra el fragmento.  
  
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
  
6.  Guarde el fragmento.  
  
7.  Abra un proyecto de Visual Basic y agregue el fragmento.  
  
8.  Verá una instrucción de importaciones al principio del archivo de código:  
  
    ```  
    Imports System.Windows.Forms  
  
    ```  
  
9. Consulte las propiedades del proyecto.  La pestaña Referencias incluye una referencia a ystem.Windows.Forms.dll.  
  
### Adición de reemplazos  
  
1.  Puede que desee que partes de sus fragmentos de código se reemplacen por el usuario, por ejemplo, si agrega una variable y desea que el usuario la reemplace por otra del proyecto actual.  Puede proporcionar dos tipos de reemplazos: literales y objetos.  Los literales son cadenas de algún tipo \(literales de cadena, nombres de variable o representaciones de cadena de valores numéricos\).  Los objetos son instancias de algún tipo distinto de una cadena.  En este procedimiento declarará un reemplazo literal y reemplazo de objeto, y cambiará el código para hacer referencia a estos reemplazos.  
  
2.  Abra el fragmento.  
  
3.  Este ejemplo utiliza una cadena de conexión SQL, por lo que tiene que cambiar los elementos Importaciones y Referencias para agregar las referencias adecuadas:  
  
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
  
4.  Para declarar un reemplazo literal para la cadena de conexión SQL, agregue un elemento de declaraciones debajo del elemento del fragmento de código, y en él agregue un elemento literal con los subelementos para el identificador, la información sobre herramientas y el valor predeterminado para el reemplazo:  
  
    ```  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
    </Declarations>  
  
    ```  
  
5.  Para declarar un reemplazo de objeto para la conexión de SQL, agregue un elemento de objeto dentro del elemento de declaraciones y agregue subelementos para el identificador, el tipo de objeto,la información sobre herramientas y el valor predeterminado.  El elemento Declaraciones resultante debería ser similar a lo siguiente:  
  
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
  
6.  En la sección de código, haga referencia a los reemplazos mediante signos $ alrededor del texto, por ejemplo `$reemplazo$`:  
  
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
  
7.  Guarde el fragmento.  
  
8.  Abra un proyecto de Visual Basic y agregue el fragmento.  
  
9. El código debe tener el aspecto que se indica a continuación, donde los reemplazos `Cadena de conexión SQL` y `dcConnection` se resaltan en naranja claro.  Presione TAB para navegar hacia delante y hacia atrás.  
  
    ```  
    Dim daCustomers As SqlDataAdapter  
    Dim selectCommand As SqlCommand  
  
    daCustomers = New SqlClient.SqlDataAdapter()  
    selectCommand = New SqlClient.SqlCommand("SQL connection string")  
    daCustomers.SelectCommand = selectCommand  
    daCustomers.SelectCommand.Connection = dcConnection  
  
    ```  
  
## Vea también  
 [Referencia de esquemas de fragmentos de código](../ide/code-snippets-schema-reference.md)