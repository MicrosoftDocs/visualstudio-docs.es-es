---
title: Procedimiento Seleccionar los esquemas XML que se van a usar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41f830214b20df24587cf902e6b180e8a43a8cd3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007411"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Procedimiento Selección de los esquemas XML que se van a usar

El editor XML proporciona una caché de esquema que se encuentra en la *%VSInstallDir%\xml\Schemas* directory. La caché de esquema incluye esquemas XML muy conocidos que se utilizan en IntelliSense y en la validación de documentos XML.

Use la **esquemas** propiedad para seleccionar uno o varios XML (XSD) esquemas de documento. Puede seleccionar los esquemas de la caché de esquema o en otro lugar.

Los esquemas especificados se guardan en un archivo de opciones de usuario de solución (oculto) (. *suo*), junto con todo el XML de las propiedades de documento. Como resultado, no tiene que volver a escribir estos valores la próxima vez que abra la solución.

> [!NOTE]
> El editor puede validar con un esquema en línea o un esquema al que hace referencia el `xsd:schemaLocation` atributo. Para obtener más información, consulte [validación de documentos XML](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Para seleccionar un esquema XML de la caché de esquema

1. Abra un archivo en el Editor XML.

2. En la ventana Propiedades del documento, haga clic en el **esquemas** campo. Cuando el botón Examinar (...) aparece, haga clic en él.

   ![Propiedad de esquemas de un archivo XML](media/properties-schemas.png)

   El [cuadro de diálogo esquemas XML](xml-schemas-dialog-box.md) se abre. El cuadro de diálogo enumera todos los esquemas con un. *xsd* extensión en la caché de esquema (incluidos los esquemas que se hace referenciados en el *catalog.xml* archivo) y también cualquier esquema que está en la solución actual, abrir en Visual Studio, hace referencia en un `xsd:schemaLocation` atributo o hace referencia en el **esquemas** propiedad.

3. Seleccione los esquemas que desea utilizar en la validación mediante una de las siguientes acciones:

   - Seleccione un esquema que aparece en el **esquemas XML** cuadro de diálogo, haga clic en el **Use** columna y, a continuación, seleccione **utilizar este esquema**.

     -o bien-

   - Seleccione varios esquemas que aparecen en la **esquemas XML** cuadro de diálogo y, a continuación, con el botón secundario y seleccione **utilizar este esquema**.

4. Elija **Aceptar**.

   La lista de esquemas seleccionados se copia en el **esquemas** propiedad de documento.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Para agregar un esquema XML a la caché de esquema

1. En la ventana Propiedades del documento, haga clic en el botón en el **esquemas** campo.

2. Haga clic en **Agregar**.

   El **Abrir esquema XSD** abre el cuadro de diálogo.

3. Busque y seleccione los esquemas que se van a agregar a la caché de esquema.

4. Haga clic en **Abrir**.

   Los esquemas se agregan a la caché de esquema y el **Use** el valor de columna se establece en **utilizar este esquema**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Para eliminar un esquema XML de la caché de esquema

1. En la ventana Propiedades del documento, haga clic en el botón en el **esquemas** campo.

2. Seleccione el esquema para quitar y, a continuación, haga clic en **quitar**.

   El esquema se quita de la caché de esquema en memoria, pero no del sistema de archivos.

   > [!NOTE]
   > Si todavía tiene una referencia al esquema a través de un `schemaLocation` atributo o una coincidencia con `targetNamespace` , a continuación, **quitar** no funcionarán en esta situación debido a la asociación automática. En este caso, se recomienda que marque el esquema como **no utilizar esquemas seleccionados** en el **usar** columna.

## <a name="see-also"></a>Vea también

- [Caché de esquema](../xml-tools/schema-cache.md)
- [Cuadro de diálogo de esquemas XML](../xml-tools/xml-schemas-dialog-box.md)
- [Editor XML](../xml-tools/xml-editor.md)