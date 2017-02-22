---
title: "Crear fragmentos de c&#243;digo XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Crear fragmentos de c&#243;digo XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El Editor XML se puede utilizar para crear nuevos fragmentos XML.El editor incluye un fragmento XML, llamado "Fragmento", que es un fragmento reutilizable que permite la creación de nuevos fragmentos XML.  
  
## Para crear un nuevo fragmento XML  
 Para crear un nuevo fragmento de código XML, cree un nuevo archivo XML y utilice la característica **Insertar fragmento**.  
  
1.  En el menú **Archivo**, haga clic en **Nuevo** y seleccione **Archivo**.  
  
2.  Haga clic en **Archivo XML** y, a continuación, seleccione **Abrir**.  
  
3.  Haga clic con el botón secundario en el panel del editor y seleccione **Insertar fragmento**.  
  
4.  Seleccione **Fragmento** en la lista y presione INREO.  
  
5.  Realice los cambios que considere oportunos en el nuevo fragmento.  
  
6.  En el menú **Archivo**, seleccione **Guardar ArchivoXML.xml**.  
  
     Aparece el cuadro de diálogo **Guardar archivo como**.  
  
7.  Especifique el nombre del nuevo fragmento y seleccione **Archivos de fragmento** en la ventana desplegable **Guardar como tipo**.  
  
8.  Utilice la lista desplegable **Guardar en** para cambiar la ubicación del archivo a la carpeta My Documents\\Visual Studio 2005\\Code Snippets\\XML\\My XML Snippets y, a continuación, presione **Guardar**.  
  
## Descripción del fragmento  
 En esta sección se describen algunos de los elementos principales del fragmento reutilizable.Para obtener más información acerca de los elementos de esquema que se utilizan en los fragmentos XML, vea [Referencia de esquemas de fragmentos de código](../ide/code-snippets-schema-reference.md).  
  
### Elemento SnippetType  
 El editor admite dos tipos de fragmentos:  
  
```  
<SnippetTypes>  
  <SnippetType>SurroundsWith</SnippetType>  
  <SnippetType>Expansion</SnippetType>  
</SnippetTypes>  
```  
  
 El tipo `Expansion` determina si aparecerá el fragmento al invocar el comando **Insertar fragmento**.El tipo `SurroundsWith` determina si aparecerá el fragmento al invocar el comando **Rodear con**.  
  
### Elemento Code  
 El elemento `Code` define el texto XML que se insertará cuando se invoque el fragmento.  
  
> [!NOTE]
>  El texto del fragmento XML se debe incluir en una sección `<![CDATA[...]]>`.  
  
 Este es el elemento `Code` que crea el fragmento reutilizable.  
  
```  
<Code Language="XML">  
  <![CDATA[<test>  
  <name>$name$</name>  
  $selected$ $end$</test>]]>  
</Code>  
```  
  
 El elemento `Code` incluye tres variables.  
  
-   $name$ es una variable definida por el usuario.Crea un elemento `name`, que tiene un valor editable que adopta "name" como valor predeterminado.Las variables definidas por el usuario se definen mediante el elemento `Literal`.  
  
-   $selected$ es una variable predefinida.Representa el texto que se ha seleccionado en el Editor XML antes de invocar el fragmento.La colocación de esta variable determina dónde aparece el texto seleccionado en el fragmento de código que rodea esa selección.  
  
-   $end$ es una variable predefinida.Cuando el usuario presiona INTRO para terminar de editar los campos de fragmento de código, esta variable determina el lugar al que se mueve el carácter de intercalación \(^\).  
  
 El elemento `Code` anterior inserta el siguiente texto XML:  
  
```  
<test>  
  <name>name</name>  
</test>  
```  
  
 El valor del elemento name se marca como una región editable.  
  
### Elemento Literal  
 El elemento `Literal` se utiliza para identificar el texto de sustitución que se puede personalizar una vez que se ha insertado en el archivo.Por ejemplo, las cadenas de literales, los valores numéricos y algunos nombres de variables se pueden declarar como literales.Se puede definir un número cualquiera de literales en el fragmento XML y hacer referencia a ellos varias veces desde dentro del fragmento.A continuación se muestra un ejemplo de un elemento `Literal` que define una variable $name$ cuyo valor predeterminado es "name".  
  
```  
<Literal>  
  <ID>name</ID>  
  <Default>name</Default>  
</Literal  
```  
  
 Los literales también pueden hacer referencia a funciones.El Editor XML incluye una función llamada **Buscar prefijo**.La función **Buscar prefijo** busca el identificador URI del espacio de nombres en cuestión desde la ubicación del documento XML desde la que se invoca este fragmento y devuelve, si lo hay, el prefijo del espacio de nombres definido para dicho espacio, e incluye dos puntos \(:\) en ese nombre.A continuación se muestra un ejemplo de un elemento `Literal` que utiliza la función **Buscar prefijo**.  
  
```  
<Literal Editable="false">  
   <ID>prefix</ID>  
   <Function>LookupPrefix("namespaceURI")</Function>  
</Literal>  
```  
  
 Luego, la variable $prefix$ puede utilizarse en cualquier parte del fragmento XML.  
  
## Vea también  
 [Fragmentos de código XML](../xml-tools/xml-snippets.md)   
 [Cómo: Usar fragmentos XML](../xml-tools/how-to-use-xml-snippets.md)   
 [Cómo: Generar un fragmento XML a partir de un esquema XML](../Topic/How%20to:%20Generate%20an%20XML%20Snippet%20From%20an%20XML%20Schema.md)