---
title: 'Cómo: Seleccionar los esquemas XML que se van a usar'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 275def786a93d42e6b8e110d3b3d785a24e948b1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601908"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Cómo: seleccionar los esquemas XML que se van a usar

El editor XML proporciona una caché de esquemas que se encuentra en el directorio *%VSInstallDir%\xml\Schemas* La caché de esquema incluye esquemas XML muy conocidos que se utilizan en IntelliSense y en la validación de documentos XML.

Utilice la propiedad de documento **esquemas** para seleccionar uno o varios esquemas del lenguaje de definición de esquemas XML (XSD). Puede seleccionar esquemas en la caché de esquemas o en otro lugar.

Los esquemas que especifique se guardan en un archivo de opciones de usuario de la solución (oculto) (. *suo*), junto con todas las demás propiedades de documento XML. Como resultado, no tiene que volver a escribir estos valores la próxima vez que abra la solución.

> [!NOTE]
> El editor puede validar mediante un esquema insertado o un esquema al que se hace referencia mediante el atributo `xsd:schemaLocation`. Para obtener más información, vea [validación de documentos XML](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Para seleccionar un esquema XML de la caché de esquema

1. Abra un archivo en el Editor XML.

2. En la ventana Propiedades del documento, haga clic en el campo **esquemas** . Cuando aparezca el botón Examinar (...), haga clic en él.

   ![Propiedad schemas para un archivo XML](media/properties-schemas.png)

   Se abrirá el [cuadro de diálogo esquemas XML](xml-schemas-dialog-box.md) . En el cuadro de diálogo se enumeran todos los esquemas con. extensión *xsd* en la caché de esquema (incluidos los esquemas a los que se hace referencia en el archivo *Catalog. XML* ) y también cualquier esquema de la solución actual, abierto en Visual Studio, al que se hace referencia en un atributo `xsd:schemaLocation` o al que se hace referencia en los **esquemas** propiedad.

3. Seleccione los esquemas que desea utilizar en la validación mediante una de las siguientes acciones:

   - Seleccione un esquema de la lista en el cuadro de diálogo **esquemas XML** , haga clic en la columna **usar** y, a continuación, seleccione **usar este esquema**.

     o bien

   - Seleccione varios esquemas en el cuadro de diálogo **esquemas XML** y, a continuación, haga clic con el botón secundario y seleccione **utilizar este esquema**.

4. Elija **Aceptar**.

   La lista de esquemas seleccionados se vuelve a copiar en la propiedad de documento **esquemas** .

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Para agregar un esquema XML a la caché de esquema

1. En la ventana Propiedades del documento, haga clic en el botón del campo **esquemas** .

2. Haga clic en **Agregar**.

   Se abre el cuadro de diálogo **abrir esquema XSD** .

3. Busque y seleccione los esquemas que se van a agregar a la caché de esquema.

4. Haga clic en **Abrir**.

   Los esquemas se agregan a la caché de esquema y el valor **usar** columna está establecido para **utilizar este esquema**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Para eliminar un esquema XML de la caché de esquema

1. En la ventana Propiedades del documento, haga clic en el botón del campo **esquemas** .

2. Seleccione el esquema que desea quitar y, a continuación, haga clic en **quitar**.

   El esquema se quita de la caché de esquema en memoria, pero no del sistema de archivos.

   > [!NOTE]
   > Si todavía tiene una referencia al esquema a través de un atributo de `schemaLocation` o una coincidencia `targetNamespace`, entonces **quitar** no funcionará en esta situación debido a la Asociación automática. En este caso, se recomienda marcar el esquema como **no usar esquemas seleccionados** en la columna **usar** .

## <a name="see-also"></a>Vea también

- [Caché de esquema](../xml-tools/schema-cache.md)
- [Esquemas XML (cuadro de diálogo)](../xml-tools/xml-schemas-dialog-box.md)
- [Editor XML](../xml-tools/xml-editor.md)