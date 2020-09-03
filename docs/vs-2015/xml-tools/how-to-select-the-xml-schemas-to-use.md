---
title: 'Cómo: seleccionar los esquemas XML que se van a usar | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f607d500bfcb8a745bfb129490d2c2b09c6b105c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666504"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Procedimiento Seleccionar los esquemas XML que se van a usar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El Editor XML proporciona una caché de esquemas que está ubicada en el directorio %InstallDir%\Xml\Schemas. La caché de esquema incluye esquemas XML muy conocidos que se utilizan en IntelliSense y en la validación de documentos XML.

 La propiedad de documento **esquemas** se utiliza para seleccionar uno o varios esquemas del lenguaje de definición de esquemas XML (XSD) que se van a utilizar. Permite seleccionar esquemas de la caché de esquema o especificar un esquema que no está ubicado en la caché.

 Los esquemas especificados se guardan en el archivo oculto de opciones del usuario de la solución (.suo), junto con todas las demás propiedades de documento XML. Por tanto, no es necesario que vuelva a escribir estos valores la próxima vez que abra la solución.

> [!NOTE]
> El editor puede realizar la validación mediante un esquema alineado o un esquema al que se haga referencia en el atributo `xsd:schemaLocation`. Para obtener más información, vea [validación de documentos XML](../xml-tools/xml-document-validation.md).

### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Para seleccionar un esquema XML de la caché de esquema

1. Abra un archivo en el Editor XML.

2. En la ventana de propiedades del documento, haga clic en el botón del campo **Esquemas**.

    Se muestra el cuadro de diálogo **esquemas XML** . En el cuadro de diálogo se enumeran todos los esquemas con una extensión. xsd en la caché de esquemas (incluidos los esquemas a los que se hace referencia en el archivo catalog.xml) y también cualquier esquema que esté en la solución actual, abierto en Visual Studio, al que se hace referencia en un atributo o al que se `xsd:schemaLocation` hace referencia en la propiedad **schemas** .

3. Seleccione los esquemas que desea utilizar en la validación mediante una de las siguientes acciones:

   - Seleccione un esquema que aparece en el cuadro de diálogo **Esquemas XML**, haga clic en la columna **Usar** y, a continuación, seleccione **Utilizar este esquema**.

     o bien

   - Seleccione varios esquemas enumerados en el cuadro de diálogo **esquemas XML** , haga clic con el botón secundario y seleccione **usar este esquema**.

4. Haga clic en **Aceptar**.

    La lista de esquemas seleccionados se copia de nuevo en la propiedad de documento **Esquemas**.

### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Para agregar un esquema XML a la caché de esquema

1. En la ventana de propiedades del documento, haga clic en el botón del campo **Esquemas**.

2. Haga clic en **Agregar**.

     Se abrirá el cuadro de diálogo **abrir esquema XSD** .

3. Busque y seleccione los esquemas que se van a agregar a la caché de esquema.

4. Haga clic en **Abrir**.

     Los esquemas agregados a la caché de esquema y es el valor de la columna **usar** establecido para **utilizar este esquema**.

### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Para eliminar un esquema XML de la caché de esquema

1. En la ventana de propiedades del documento, haga clic en el botón del campo **Esquemas**.

2. Seleccione el esquema que quiere quitar y haga clic en **Quitar**.

     El esquema se quita de la caché de esquema en memoria, pero no del sistema de archivos.

    > [!NOTE]
    > Si todavía existe una referencia al esquema a través de un atributo `schemaLocation` o una coincidencia con `targetNamespace`, entonces **Quitar** no funcionará en esta situación debido a una asociación automática. En este caso, se recomienda marcar el esquema como **No utilizar esquemas seleccionados** en la columna **Usar**.

## <a name="see-also"></a>Consulte también
 [Editor XML](../xml-tools/xml-editor.md) del [cuadro de diálogo esquemas XML](../xml-tools/xml-schemas-dialog-box.md) de la [caché de esquema](../xml-tools/schema-cache.md)
