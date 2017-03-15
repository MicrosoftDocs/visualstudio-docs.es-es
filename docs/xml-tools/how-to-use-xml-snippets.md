---
title: "C&#243;mo: Usar fragmentos XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# C&#243;mo: Usar fragmentos XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede invocar fragmentos XML mediante los dos siguientes comandos del menú contextual del Editor XML.El comando **Insertar fragmento** inserta el fragmento XML en la posición del cursor.El comando **Delimitar con** ajusta el fragmento XML alrededor del texto seleccionado.Cada fragmento XML tiene designados tipos de fragmentos.Los tipos de fragmentos determinan si el fragmento está disponible con el comando **Insertar fragmento**, el comando **Delimitar con**, o ambos.  
  
 Una vez que el fragmento XML se ha agregado al editor, todos los campos editables del fragmento se resaltan en amarillo y el cursor se coloca en el primer campo editable.  
  
## Insertar fragmento  
 Los siguientes procedimientos describen cómo tener acceso al comando **Insertar fragmento**.  
  
> [!NOTE]
>  El comando **Insertar fragmento** también se encuentra disponible mediante el método abreviado del teclado \(CTRL\+K, luego CTRL\+X\).  
  
#### Para insertar fragmentos desde el menú contextual  
  
1.  Coloque el cursor en el lugar en el que desea insertar el fragmento XML.  
  
2.  Haga clic con el botón secundario y seleccione **Insertar fragmento**.  
  
     Se muestra una lista de fragmentos XML disponibles.  
  
3.  Seleccione un fragmento de la lista con el mouse o escriba el nombre del fragmento y presione la tecla TAB o INTRO.  
  
#### Para insertar fragmentos con el menú IntelliSense  
  
1.  Coloque el cursor en el lugar en el que desea insertar el fragmento XML.  
  
2.  En el menú **Edición**, seleccione **IntelliSense** y, a continuación, seleccione **Insertar fragmento**.  
  
     Se muestra una lista de fragmentos XML disponibles.  
  
3.  Seleccione un fragmento de la lista con el mouse o escriba el nombre del fragmento y presione la tecla TAB o INTRO.  
  
#### Para insertar fragmentos mediante la lista de palabras completas de IntelliSense  
  
1.  Coloque el cursor en el lugar en el que desea insertar el fragmento XML.  
  
2.  Comience a escribir el fragmento XML que desea agregar al archivo.Si la finalización automática está activada, se muestra la lista de palabras completas de IntelliSense.Si no aparece, presione CTRL\+BARRA ESPACIADORA para activarla.  
  
3.  Seleccione el fragmento XML de la lista de palabras completas.  
  
4.  Presione TAB, TAB para invocar el fragmento XML.  
  
> [!NOTE]
>  Puede haber casos en los que el fragmento XML no se llegue a invocar.Por ejemplo, si intenta insertar un elemento `xs:complexType` dentro de un nodo `xs:element`, el editor no genera un fragmento XML.Cuando un elemento `xs:complexType` se utiliza dentro de un nodo `xs:element`, no están los atributos o subelementos necesarios, así que el editor no tiene datos que insertar.  
  
#### Para insertar fragmentos con el nombre de acceso directo  
  
1.  Coloque el cursor en el lugar en el que desea insertar el fragmento XML.  
  
2.  Escriba `<` en el panel del editor.  
  
3.  Presione ESC para cerrar la lista de palabras completas de IntelliSense.  
  
4.  Escriba el nombre de acceso directo del fragmento y presione TAB para invocar el fragmento XML.  
  
## Delimitar con  
 Los siguientes procedimientos describen cómo tener acceso al comando **Delimitar con**.  
  
> [!NOTE]
>  El comando **Delimitar con** también se encuentra disponible mediante el método abreviado del teclado \(CTRL\+K, luego CTRL\+S\).  
  
#### Para utilizar este comando desde el menú de acceso directo  
  
1.  Seleccione el texto que se va a rodear en el Editor XML.  
  
2.  Haga clic con el botón secundario y seleccione **Delimitar con**.  
  
     Se muestra una lista de bordes disponibles con fragmentos XML.  
  
3.  Seleccione un fragmento de la lista con el mouse o escriba el nombre del fragmento y presione la tecla TAB o INTRO.  
  
#### Para utilizar este comando desde el menú IntelliSense  
  
1.  Seleccione el texto que se va a rodear en el Editor XML.  
  
2.  En el menú **Edición**, seleccione **IntelliSense** y, a continuación, seleccione **Delimitar con**.  
  
     Se muestra una lista de bordes disponibles con fragmentos XML.  
  
3.  Seleccione un fragmento de la lista con el mouse o escriba el nombre del fragmento y presione la tecla TAB o INTRO.  
  
## Uso de fragmentos XML  
 Una vez elegido un fragmento XML, el texto del fragmento de código se inserta automáticamente en la posición del cursor.Todos los campos editables del fragmento se resaltan y el primero de estos campos se selecciona automáticamente.Al campo actualmente seleccionado se le aplica la conversión boxing.  
  
 Cuando se selecciona un campo, puede escribir un nuevo valor para el mismo.Si presiona la tecla TAB recorrerá los campos editables del fragmento; si presiona MAYÚS\+TAB los recorrerá en orden inverso.Al hacer clic en un campo, el cursor se coloca en dicho campo, y al hacer doble clic en él se selecciona.Cuando un campo está resaltado, podría mostrarse información sobre herramientas, que ofrece una descripción del campo.  
  
 Solo es editable la primera ocurrencia de un campo dado.Cuando ese campo está resaltado, las demás ocurrencias de dicho campo se destacan.Si cambia el valor de un campo editable, ese campo cambia en cualquier parte en la que se utilice en el fragmento.  
  
 Si presiona INTRO o ESC se cancela la edición de los campos y el editor vuelve a su estado normal.  
  
 Los colores predeterminados de los campos editables de fragmento de código se pueden cambiar si modifica la opción Campo de fragmento de código del panel **Fuentes y colores** del cuadro de diálogo **Opciones**.Para obtener más información, vea [Cómo: Cambiar las fuentes y los colores del editor](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).  
  
## Vea también  
 [Fragmentos de código XML](../xml-tools/xml-snippets.md)   
 [Cómo: Generar un fragmento XML a partir de un esquema XML](../Topic/How%20to:%20Generate%20an%20XML%20Snippet%20From%20an%20XML%20Schema.md)   
 [Crear fragmentos de código XML](../xml-tools/how-to-create-xml-snippets.md)