---
title: 'Cómo: crear fragmentos XML | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 38bec6de97a0b9d38891046a1a6b57f4d31541bf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818164"
---
# <a name="how-to-create-xml-snippets"></a>Crear fragmentos de código XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
El Editor XML se puede utilizar para crear nuevos fragmentos XML. El editor incluye un fragmento XML, llamado "Fragmento", que es un fragmento reutilizable que permite la creación de nuevos fragmentos XML.  
  
## <a name="to-create-a-new-xml-snippet"></a>Para crear un nuevo fragmento XML  
 Para crear un nuevo código XML fragmento de código, cree un nuevo archivo XML y usar el **Insertar fragmento de código** característica.  
  
1.  En el **archivo** menú, haga clic en **New** y, a continuación, haga clic en **archivo**.  
  
2.  Haga clic en **archivo XML** y, a continuación, haga clic en **abierto**.  
  
3.  Haga clic en el panel del editor y seleccione **Insertar fragmento de código**.  
  
4.  Seleccione **fragmento** en la lista y presione ENTRAR.  
  
5.  Realice los cambios que considere oportunos en el nuevo fragmento.  
  
6.  Desde el **archivo** menú, seleccione **guardar archivoXml.XML**.  
  
     El **Guardar archivo como** se muestra el cuadro de diálogo.  
  
7.  Escriba el nombre del nuevo fragmento y seleccione **archivos de fragmento** desde el **Guardar como tipo** ventana desplegable.  
  
8.  Use la **guardar en** lista desplegable para cambiar la ubicación del archivo a la carpeta de Mis documentos\Visual Studio 2005\Code Snippets\XML\My XML Snippets y, a continuación, presione **guardar**.  
  
## <a name="snippet-description"></a>Descripción del fragmento  
 En esta sección se describen algunos de los elementos principales del fragmento reutilizable. Para obtener más información acerca de los elementos del esquema utilizado por los fragmentos de código XML, vea [referencia de esquemas de fragmentos de código](../ide/code-snippets-schema-reference.md).  
  
### <a name="snippettype-element"></a>Elemento SnippetType  
 El editor admite dos tipos de fragmentos:  
  
```  
<SnippetTypes>  
  <SnippetType>SurroundsWith</SnippetType>  
  <SnippetType>Expansion</SnippetType>  
</SnippetTypes>  
```  
  
 El `Expansion` tipo determina si aparecerá el fragmento al invocar el **Insertar fragmento de código** comando. El `SurroundsWith` tipo determina si aparecerá el fragmento al invocar el **rodear con** comando.  
  
### <a name="code-element"></a>Elemento de código  
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
  
- $name$ es una variable definida por el usuario. Crea un elemento `name`, que tiene un valor editable que adopta "name" como valor predeterminado. Las variables definidas por el usuario se definen mediante el elemento `Literal`.  
  
- $selected$ es una variable predefinida. Representa el texto que se ha seleccionado en el Editor XML antes de invocar el fragmento. La colocación de esta variable determina dónde aparece el texto seleccionado en el fragmento de código que rodea esa selección.  
  
- $end$ es una variable predefinida. Cuando el usuario presiona INTRO para terminar de editar los campos de fragmento de código, esta variable determina el lugar al que se mueve el carácter de intercalación (^).  
  
  El elemento `Code` anterior inserta el siguiente texto XML:  
  
```  
<test>  
  <name>name</name>  
</test>  
```  
  
 El valor del elemento name se marca como una región editable.  
  
### <a name="literal-element"></a>Elemento Literal  
 El elemento `Literal` se utiliza para identificar el texto de sustitución que se puede personalizar una vez que se ha insertado en el archivo. Por ejemplo, las cadenas de literales, los valores numéricos y algunos nombres de variables se pueden declarar como literales. Se puede definir un número cualquiera de literales en el fragmento XML y hacer referencia a ellos varias veces desde dentro del fragmento. A continuación se muestra un ejemplo de un elemento `Literal` que define una variable $name$ cuyo valor predeterminado es "name".  
  
```  
<Literal>  
  <ID>name</ID>  
  <Default>name</Default>  
</Literal  
```  
  
 Los literales también pueden hacer referencia a funciones. El Editor XML incluye una función denominada **LookupPrefix**. El **LookupPrefix** función busca el URI de espacio de nombres determinado desde la ubicación en el documento XML que este fragmento de código se invoca desde y devuelve el prefijo de espacio de nombres que se define para ese espacio de nombres, si la hubiera, e incluye los dos puntos (:) en ese nombre. El siguiente es un ejemplo de un `Literal` elemento que usa el **LookupPrefix** función.  
  
```  
<Literal Editable="false">  
   <ID>prefix</ID>  
   <Function>LookupPrefix("namespaceURI")</Function>  
</Literal>  
```  
  
 Luego, la variable $prefix$ puede utilizarse en cualquier parte del fragmento XML.  
  
## <a name="see-also"></a>Vea también  
 [Fragmentos XML](../xml-tools/xml-snippets.md)   
 [Cómo: utilizar fragmentos XML](../xml-tools/how-to-use-xml-snippets.md)   
 [Cómo: Generar un fragmento de código XML a partir de un esquema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)



