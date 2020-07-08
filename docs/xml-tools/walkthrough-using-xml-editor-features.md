---
title: 'Tutorial: Uso de características del Editor XML'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1cebf6f7621fb5fada37b8e4592efd429bdc85e6
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817403"
---
# <a name="walkthrough-use-xml-editor-features"></a>Tutorial: Uso de características del editor XML

En este tutorial se indican los pasos para crear un nuevo documento XML. El tutorial también utiliza algunas de las características del Editor XML que lo convierten en una valiosa herramienta para la creación de XML.

> [!NOTE]
> Antes de comenzar el tutorial, guarde el archivo *hireDate.xsd* (que se incluye a continuación en este tema) en el equipo local.

## <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Para crear un archivo XML nuevo y asociarlo con un esquema XML

1. En el menú **Archivo**, seleccione **Nuevo** y haga clic en **Archivo**.

2. Seleccione **Archivo XML** en el panel **Plantillas** y haga clic en **Abrir**.

     Se abre un nuevo archivo en el editor. El archivo contiene una declaración XML predeterminada, `<?xml version="1.0" encoding="utf-8">`.

3. En la ventana Propiedades del documento, haga clic en el botón Examinar ( **…** ) en el campo **Esquemas**.

     Aparece el cuadro de diálogo **Esquemas XSD**.

4. Haga clic en **Agregar**.

     Aparece el cuadro de diálogo **Abrir esquema XSD**.

5. Seleccione el archivo *hireDate.xsd* y haga clic en **Abrir**.

6. Haga clic en **Aceptar**.

     El esquema XML está ahora asociado con el documento XML. El esquema XML se utiliza para validar el documento. IntelliSense también lo utiliza para llenar la lista de miembros de elementos válidos.

## <a name="to-add-data"></a>Para agregar datos

1. Escriba `<` en el panel del editor.

     La lista de miembros muestra los elementos posibles:

    - **!--** para agregar un comentario.

    - **!DOCTYPE** para agregar un tipo de documento.

    - **?** para agregar una instrucción de procesamiento.

    - **employee** para agregar el elemento raíz.

2. Seleccione **&lt;!--** para agregar un nodo de comentario y presione **ENTRAR**.

     El editor inserta una etiqueta de cierre de comentario y coloca el cursor entre las etiquetas de comentario de apertura y de cierre.

3. Escriba **Probar archivo XML**.

4. En una línea nueva, escriba `<` y seleccione **employee** en la lista de miembros.

     El editor agrega el comienzo de un elemento XML, `<employee`. Llegados a este punto, puede agregar atributos al elemento o bien cerrar la etiqueta de apertura escribiendo `>`.

5. Escriba `>` para cerrar la etiqueta.

6. El editor agrega la etiqueta de cierre. Ésta se agrega con un subrayado ondulado que indica un error de validación. La **información sobre herramientas** muestra el mensaje: **El contenido del elemento "employee" no está completo. Se esperaba "ID".**

7. Escriba `<` y seleccione **ID** en la lista de miembros. A continuación, escriba `>`.

     El editor agrega el elemento XML, `<ID></ID>`, y coloca el cursor después de la etiqueta de apertura de ID.

8. Escriba **abc**.

     El texto **abc** presenta un subrayado ondulado. La **información sobre herramientas** muestra el mensaje: **El elemento "ID" tiene un valor que no es válido para su tipo de datos**.

9. Haga clic con el botón derecho en el elemento ID y seleccione **Ir a definición**.

     El editor abre el archivo *hireDate.xsd* en una nueva ventana de documento y coloca el cursor en la definición del elemento de esquema ID.

10. Vuelva al archivo XML y sustituya el texto **abc** por **123**.

     El subrayado ondulado y la **información sobre herramientas** desaparecen bajo el valor del elemento ID. La **información sobre herramientas** de la etiqueta final de empleado muestra ahora el mensaje: **El contenido del elemento "employee" no está completo. Se esperaba "hire-date"** .

11. Coloque el cursor después de la etiqueta final de ID, escriba `<`, seleccione **hire-date** en la lista de miembros y, a continuación, escriba `>`.

     El editor agrega el elemento XML, `<hire-date></hire-date>`, y coloca el cursor después de la etiqueta de apertura de fecha-contratación.

12. Escriba **2003-01-10** para el valor hire-date.

## <a name="to-format-the-xml-document"></a>Para dar formato al documento XML

- Seleccione el botón **Dar formato al documento** en la barra del Editor XML o presione **Ctrl**+**E**,**D**.

   ![Botón Dar formato al documento XML en Visual Studio](media/format-xml-document.png)

   El documento XML adquiere un nuevo formato.

## <a name="to-save-the-xml-document"></a>Para guardar el documento XML

1. En el menú **Archivo**, seleccione **Guardar como**.

     Aparece el cuadro de diálogo **Guardar archivo como**. El nombre de archivo predeterminado es *"XMLFile1"* .

2. Especifique el nombre de archivo y la ubicación del documento XML y haga clic en **Guardar**.

## <a name="hiredatexsd-file"></a>Archivo hireDate.xsd

El tutorial utiliza el archivo de esquema siguiente:

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
