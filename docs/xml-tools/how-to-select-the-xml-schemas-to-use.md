---
title: Procedimiento Seleccionar los esquemas XML que se van a usar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2acafe0c782b39bb7aa345b5456df7238703cb20
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592651"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Procedimiento Selección de los esquemas XML que se van a usar

El Editor XML proporciona una caché de esquemas que se encuentra en el directorio *%VSInstallDir%\xml\Schemas*. La caché de esquema incluye esquemas XML muy conocidos que se utilizan en IntelliSense y en la validación de documentos XML.

Use la propiedad de documento **Esquemas** para seleccionar uno o varios esquemas de lenguaje de definición de esquema XML (XSD). Puede seleccionar esquemas en la caché de esquemas o en otro lugar.

Los esquemas especificados se guardan en un archivo (oculto) de opciones del usuario de la solución (.*suo*), junto con todas las demás propiedades de documento XML. Por tanto, no es necesario que vuelva a escribir estos valores la próxima vez que abra la solución.

> [!NOTE]
> El editor puede realizar la validación mediante un esquema alineado o un esquema al que se haga referencia en el atributo `xsd:schemaLocation`. Para más información, consulte [Validación de documentos XML](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Para seleccionar un esquema XML de la caché de esquemas

1. Abra un archivo en el Editor XML.

2. En la ventana de propiedades del documento, haga clic en el campo **Esquemas**. Cuando aparezca el botón Examinar (…), haga clic en él.

   ![Propiedad de esquemas de un archivo XML](media/properties-schemas.png)

   Se abrirá el [cuadro de diálogo Esquemas XML](xml-schemas-dialog-box.md). En el cuadro de diálogo se muestran todos los esquemas con una extensión *.xsd* en la caché de esquemas (incluidos los esquemas a los que se hace referencia en el archivo *catalog.xml*), así como los esquemas que se encuentren en la solución actual, que estén abiertos en Visual Studio, a los que se haga referencia en un atributo `xsd:schemaLocation` o a los que se haga referencia en la propiedad **Esquemas**.

3. Seleccione los esquemas que desea utilizar en la validación mediante una de las siguientes acciones:

   - Seleccione un esquema que aparece en el cuadro de diálogo **Esquemas XML**, haga clic en la columna **Usar** y, a continuación, seleccione **Utilizar este esquema**.

     o bien

   - Seleccione varios esquemas que aparecen en el cuadro de diálogo **Esquemas XML**, haga clic con el botón derecho y seleccione **Utilizar este esquema**.

4. Elija **Aceptar**.

   La lista de esquemas seleccionados se copia de nuevo en la propiedad de documento **Esquemas**.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Para agregar un esquema XML a la caché de esquemas

1. En la ventana de propiedades del documento, haga clic en el botón del campo **Esquemas**.

2. Haga clic en **Agregar**.

   Se abre el cuadro de diálogo **Abrir esquema XSD**.

3. Busque y seleccione los esquemas que se van a agregar a la caché de esquema.

4. Haga clic en **Abrir**.

   Los esquemas se agregan a la caché de esquemas y el valor de la columna **Usar** se establece en **Utilizar este esquema**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Para eliminar un esquema XML de la caché de esquemas

1. En la ventana de propiedades del documento, haga clic en el botón del campo **Esquemas**.

2. Seleccione el esquema que quiere quitar y haga clic en **Quitar**.

   El esquema se quita de la caché de esquema en memoria, pero no del sistema de archivos.

   > [!NOTE]
   > Si todavía existe una referencia al esquema a través de un atributo `schemaLocation` o una coincidencia con `targetNamespace`, entonces **Quitar** no funcionará en esta situación debido a una asociación automática. En este caso, se recomienda marcar el esquema como **No utilizar esquemas seleccionados** en la columna **Usar**.

## <a name="see-also"></a>Vea también

- [Caché de esquemas](../xml-tools/schema-cache.md)
- [Cuadro de diálogo Esquemas XML](../xml-tools/xml-schemas-dialog-box.md)
- [Editor XML](../xml-tools/xml-editor.md)
