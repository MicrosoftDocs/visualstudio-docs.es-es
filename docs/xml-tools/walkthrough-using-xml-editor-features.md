---
title: 'Tutorial: usar las características del editor XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2cf35730b70fc8c8bbec392c73b444b6e8e0aaa
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592469"
---
# <a name="walkthrough-use-xml-editor-features"></a>Tutorial: usar las características del editor XML

En este tutorial se indican los pasos para crear un nuevo documento XML. En el tutorial también se usan algunas de las características del editor XML que facilitan la creación de XML.

> [!NOTE]
> Antes de iniciar el tutorial, guarde el archivo *HireDate. xsd* (que se incluye a continuación en este tema) en el equipo local.

## <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Para crear un nuevo archivo XML y asociarlo a un esquema XML

1. En el menú **archivo** , seleccione **nuevo**y haga clic en **archivo**.

2. Seleccione **archivo XML** en el panel **plantillas** y haga clic en **abrir**.

     Se abre un nuevo archivo en el editor. El archivo contiene una declaración XML predeterminada, `<?xml version="1.0" encoding="utf-8">`.

3. En la ventana Propiedades del documento, haga clic en el botón Examinar ( **...** ) del campo **esquemas** .

     Se muestra el cuadro de diálogo **esquemas XSD** .

4. Haga clic en **Agregar**.

     Se muestra el cuadro de diálogo **abrir esquema XSD** .

5. Seleccione el archivo *HireDate. xsd* y haga clic en **abrir**.

6. Haga clic en **Aceptar**.

     El esquema XML está ahora asociado con el documento XML. El esquema XML se utiliza para validar el documento. IntelliSense también lo utiliza para llenar la lista de miembros de elementos válidos.

## <a name="to-add-data"></a>Para agregar datos

1. Escriba `<` en el panel del editor.

     La lista de miembros muestra los elementos posibles:

    - **!--** para agregar un comentario.

    - **! DOCTYPE** para agregar un tipo de documento.

    - **?** para agregar una instrucción de procesamiento.

    - **empleado** para agregar el elemento raíz.

2. Seleccione **&lt;!--** para agregar un nodo de comentario y presione **entrar**.

     El editor inserta una etiqueta de cierre de comentario y coloca el cursor entre las etiquetas de comentario de apertura y de cierre.

3. Escriba en el **archivo XML de prueba**.

4. En una nueva línea, escriba `<`y seleccione **empleado** en la lista de miembros.

     El editor agrega el comienzo de un elemento XML, `<employee`. Llegados a este punto, puede agregar atributos al elemento o bien cerrar la etiqueta de apertura escribiendo `>`.

5. Escriba `>` para cerrar la etiqueta.

6. El editor agrega la etiqueta de cierre. Ésta se agrega con un subrayado ondulado que indica un error de validación. La **información sobre herramientas** muestra el mensaje: **el elemento ' empleado ' tiene contenido incompleto. Se esperaba ' ID '** .

7. Escriba `<` y seleccione **ID** en la lista de miembros. A continuación, escriba `>`.

     El editor agrega el elemento XML, `<ID></ID>`, y coloca el cursor después de la etiqueta de apertura de ID.

8. Escriba **ABC**.

     El texto **ABC** tiene un subrayado ondulado. La **información sobre herramientas** muestra el mensaje: **el elemento ' ID ' tiene un valor no válido de acuerdo con su tipo de datos**.

9. Haga clic con el botón derecho en el elemento ID y seleccione **ir a definición**.

     El editor abre el archivo *HireDate. xsd* en una nueva ventana de documento y coloca el cursor en la definición del elemento de esquema de identificador.

10. Vuelva al archivo XML y reemplace el texto **ABC** por **123**.

     El subrayado ondulado y la **información sobre herramientas** se borran en el valor del elemento ID. La **información sobre herramientas** para la etiqueta de fin de empleado ahora muestra el mensaje: **el elemento ' empleado ' tiene contenido incompleto. Se esperaba ' fecha-contratación '** .

11. Coloque el cursor después de la etiqueta de cierre de identificador, escriba en `<`, seleccione **contratar fecha** en la lista de miembros y, a continuación, escriba en `>`.

     El editor agrega el elemento XML, `<hire-date></hire-date>`, y coloca el cursor después de la etiqueta de apertura de fecha-contratación.

12. Escriba **2003-01-10** para el valor de fecha de contratación.

## <a name="to-format-the-xml-document"></a>Para dar formato al documento XML

- Seleccione el botón **dar formato al documento** en la barra de herramientas del editor XML o presione **Ctrl**+**E**,**D**.

   ![Botón formato de documento XML en Visual Studio](media/format-xml-document.png)

   El documento XML adquiere un nuevo formato.

## <a name="to-save-the-xml-document"></a>Para guardar el documento XML

1. En el menú **Archivo** , seleccione **Guardar como**.

     Se muestra el cuadro de diálogo **Guardar archivo como** . El nombre de archivo predeterminado es *"XMLFile1"* .

2. Escriba el nombre de archivo y la ubicación del documento XML y haga clic en **Guardar**.

## <a name="hiredatexsd-file"></a>archivo hireDate. xsd

En este tutorial se usa el archivo de esquema siguiente:

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
