---
title: 'Tutorial: Usar las características del Editor XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6884f5b97d52e8d0671f1ccb73a1dabd739afee1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-using-xml-editor-features"></a>Tutorial: Usar las características del Editor XML

En este tutorial se indican los pasos para crear un nuevo documento XML. El tutorial también utiliza algunas de las características del Editor XML que lo convierten en una valiosa herramienta para la creación de XML.

> [!NOTE]
> Antes de comenzar el tutorial, guarde el archivo hireDate.xsd (que se incluye a continuación en este tema) en el equipo local.

## <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Para crear un nuevo archivo XML y asociarlo con un esquema XML

1.  En el **archivo** menú, elija **New**y haga clic en **archivo**.

2.  Seleccione **archivo XML** en el **plantillas** panel y haga clic en **abiertos**.

     Se abre un nuevo archivo en el editor. El archivo contiene una declaración XML predeterminada, `<?xml version="1.0" encoding="utf-8">`.

3.  En la ventana Propiedades del documento, haga clic en el botón Examinar (**...** ) en el **esquemas** campo.

     El **esquemas XSD** se muestra el cuadro de diálogo.

4.  Haga clic en **Agregar**.

     El **Abrir esquema XSD** se muestra el cuadro de diálogo.

5.  Seleccione el archivo hireDate.xsd y haga clic en **abiertos**.

6.  Haga clic en **Aceptar**.

     El esquema XML está ahora asociado con el documento XML. El esquema XML se utiliza para validar el documento. IntelliSense también lo utiliza para llenar la lista de miembros de elementos válidos.

## <a name="to-add-data"></a>Para agregar datos

1.  Escriba `<` en el panel del editor.

     La lista de miembros muestra los elementos posibles:

    -   **!--** para agregar un comentario.

    -   **! DOCTYPE** para agregar un tipo de documento.

    -   **?** para agregar una instrucción de procesamiento.

    -   **empleado** para agregar el elemento raíz.

2.  Seleccione **<!--** para agregar un nodo de comentario y presione ENTRAR.

     El editor inserta una etiqueta de cierre de comentario y coloca el cursor entre las etiquetas de comentario de apertura y de cierre.

3.  Escriba en **probar archivo XML**.

4.  En una línea nueva, escriba `<`y seleccione **empleado** desde la lista de miembros.

     El editor agrega el comienzo de un elemento XML, `<employee`. Llegados a este punto, puede agregar atributos al elemento o bien cerrar la etiqueta de apertura escribiendo `>`.

5.  Escriba `>` para cerrar la etiqueta.

6.  El editor agrega la etiqueta de cierre. Ésta se agrega con un subrayado ondulado que indica un error de validación. La información sobre herramientas muestra el mensaje: El contenido del elemento 'empleado' está incompleto. Se esperaba 'ID'.

7.  Tipo de `<` y seleccione **ID** en la lista de miembros. A continuación, escriba `>`.

     El editor agrega el elemento XML, `<ID></ID>`, y coloca el cursor después de la etiqueta de apertura de ID.

8.  Tipo de **abc**.

     El **abc** texto tiene un subrayado ondulado de color. La información sobre herramientas muestra el mensaje: El elemento 'ID' tiene un valor que no es válido para su tipo de datos.

9. Haga clic con el botón secundario en el elemento ID y seleccione **ir a definición**.

     El editor abre el archivo hireDate.xsd en una nueva ventana de documento y coloca el cursor en la definición del elemento de esquema ID.

10. Vuelva al archivo XML y reemplace la **abc** texto con **123**.

     El subrayado ondulado y la información sobre herramientas desaparecen bajo el valor del elemento ID. La información sobre herramientas la etiqueta de cierre del empleado ahora muestra el mensaje: El contenido del elemento 'empleado' está incompleto. Se esperaba 'fecha-contratación'.

11. Coloque el cursor después de la etiqueta de cierre de ID, escriba `<`, seleccione fecha-contratación en la lista de miembros y, a continuación, escriba `>`.

     El editor agrega el elemento XML, `<hire-date></hire-date>`, y coloca el cursor después de la etiqueta de apertura de fecha-contratación.

12. Escriba en **2003-01-10** para el valor de fecha de contratación.

## <a name="to-format-the-xml-document"></a>Para dar formato al documento XML

- Seleccione el **dar formato al documento** botón desde la barra de herramientas del Editor XML.

    El documento XML adquiere un nuevo formato.

## <a name="to-save-the-xml-document"></a>Para guardar el documento XML

1.  Desde el **archivo** menú, seleccione **Guardar como**.

     El **Guardar archivo como** se muestra el cuadro de diálogo. El nombre de archivo predeterminado es 'ArchivoXML1'.

2.  Escriba el nombre de archivo y la ubicación del documento XML y haga clic en **guardar**.

## <a name="hiredatexsd-file"></a>Archivo hireDate.xsd
 El tutorial utiliza el siguiente archivo de esquema.

```xml
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

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)