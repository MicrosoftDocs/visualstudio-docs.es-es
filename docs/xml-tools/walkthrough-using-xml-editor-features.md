---
title: "Tutorial: Usar las caracter&#237;sticas del Editor XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tutorial: Usar las caracter&#237;sticas del Editor XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tutorial se indican los pasos para crear un nuevo documento XML.El tutorial también utiliza algunas de las características del Editor XML que lo convierten en una valiosa herramienta para la creación de XML.  
  
> [!NOTE]
>  Antes de comenzar el tutorial, guarde el archivo hireDate.xsd \(que se incluye a continuación en este tema\) en el equipo local.  
  
### Para crear un nuevo archivo XML y asociarlo con un esquema XML  
  
1.  En el menú **Archivo**, seleccione **Nuevo** y haga clic en **Archivo**.  
  
2.  Seleccione **Archivo XML** en el panel **Plantillas** y haga clic en **Abrir**.  
  
     Se abre un nuevo archivo en el editor.El archivo contiene una declaración XML predeterminada, `<?xml version="1.0" encoding="utf-8">`.  
  
3.  En la ventana Propiedades del documento, haga clic en el botón Examinar \(**…**\) en el campo **Esquemas**.  
  
     Aparece el cuadro de diálogo **Esquemas XSD**.  
  
4.  Haga clic en **Agregar**.  
  
     Aparece el cuadro de diálogo **Abrir esquema XSD**.  
  
5.  Seleccione el archivo hireDate.xsd y haga clic en **Abrir**.  
  
6.  Haga clic en **Aceptar**.  
  
     El esquema XML está ahora asociado con el documento XML.El esquema XML se utiliza para validar el documento.IntelliSense también lo utiliza para llenar la lista de miembros de elementos válidos.  
  
### Para agregar datos  
  
1.  Escriba `<` en el panel del editor.  
  
     La lista de miembros muestra los elementos posibles:  
  
    -   **\!\-\-** para agregar un comentario.  
  
    -   **\!DOCTYPE** para agregar un tipo de documento.  
  
    -   **?** para agregar una instrucción de procesamiento.  
  
    -   **empleado** para agregar el elemento raíz.  
  
2.  Seleccione **\<\!\-\-** para agregar un nodo de comentario y presione INTRO.  
  
     El editor inserta una etiqueta de cierre de comentario y coloca el cursor entre las etiquetas de comentario de apertura y de cierre.  
  
3.  Escriba Probar archivo XML.  
  
4.  En una nueva línea, escriba `<` y seleccione **empleado** en la lista de miembros.  
  
     El editor agrega el comienzo de un elemento XML, `<employee`.Llegados a este punto, puede agregar atributos al elemento o bien cerrar la etiqueta de apertura escribiendo `>`.  
  
5.  Escriba `>` para cerrar la etiqueta.  
  
6.  El editor agrega la etiqueta de cierre.Ésta se agrega con un subrayado ondulado que indica un error de validación.La información sobre herramientas muestra el mensaje: El contenido del elemento 'empleado' está incompleto.Se esperaba 'ID'.  
  
7.  Escriba `<` y seleccione **ID** en la lista de miembros.A continuación, escriba `>`.  
  
     El editor agrega el elemento XML, `<ID></ID>`, y coloca el cursor después de la etiqueta de apertura de ID.  
  
8.  Escriba abc.  
  
     El texto abc presenta un subrayado ondulado.La información sobre herramientas muestra el mensaje: El elemento 'ID' tiene un valor que no es válido para su tipo de datos.  
  
9. Haga clic con el botón secundario en el elemento ID y seleccione **Ir a definición**.  
  
     El editor abre el archivo hireDate.xsd en una nueva ventana de documento y coloca el cursor en la definición del elemento de esquema ID.  
  
10. Vuelva al archivo XML y sustituya el texto abc por 123.  
  
     El subrayado ondulado y la información sobre herramientas desaparecen bajo el valor del elemento ID.La información sobre herramientas la etiqueta de cierre del empleado ahora muestra el mensaje: El contenido del elemento 'empleado' está incompleto.Se esperaba 'fecha\-contratación'.  
  
11. Coloque el cursor después de la etiqueta de cierre de ID, escriba `<`, seleccione fecha\-contratación en la lista de miembros y, a continuación, escriba `>`.  
  
     El editor agrega el elemento XML, `<hire-date></hire-date>`, y coloca el cursor después de la etiqueta de apertura de fecha\-contratación.  
  
12. Escriba 2003\-01\-10 para el valor de fecha\-contratación.  
  
### Para dar formato al documento XML  
  
1.  Seleccione el botón **Dar formato al documento** en la barra de herramientas del Editor XML.  
  
     El documento XML adquiere un nuevo formato.  
  
### Para guardar el documento XML  
  
1.  En el menú **Archivo**, seleccione **Guardar como**.  
  
     Aparece el cuadro de diálogo **Guardar archivo como**.El nombre de archivo predeterminado es 'ArchivoXML1'.  
  
2.  Especifique el nombre de archivo y la ubicación del documento XML y haga clic en **Guardar**.  
  
## Archivo hireDate.xsd  
 El tutorial utiliza el siguiente archivo de esquema.  
  
```  
<?xml version="1.0"?>  
<xs:schema attributeFormDefault="unqualified"  
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"  
     xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="employee">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="ID" type="xs:unsignedShort" />  
        <xs:element name="hire-date" type="xs:date" />  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## Vea también  
 [Editor XML](../xml-tools/xml-editor.md)