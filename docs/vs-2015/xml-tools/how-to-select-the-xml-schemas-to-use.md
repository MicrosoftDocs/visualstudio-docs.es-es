---
title: 'Cómo: seleccionar los esquemas XML que se usarán | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93f573412524619292b1966e87abeda11cc0813a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863729"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Cómo: Seleccionar los esquemas XML que se van a usar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
El Editor XML proporciona una caché de esquemas que está ubicada en el directorio %InstallDir%\Xml\Schemas. La caché de esquema incluye esquemas XML muy conocidos que se utilizan en IntelliSense y en la validación de documentos XML.  
  
 El **esquemas** propiedad de documento se utiliza para seleccionar uno o más esquemas XML que se esquema definition language (XSD) para usar. Permite seleccionar esquemas de la caché de esquema o especificar un esquema que no está ubicado en la caché.  
  
 Los esquemas especificados se guardan en el archivo oculto de opciones del usuario de la solución (.suo), junto con todas las demás propiedades de documento XML. Por tanto, no es necesario que vuelva a escribir estos valores la próxima vez que abra la solución.  
  
> [!NOTE]
>  El editor puede realizar la validación mediante un esquema alineado o un esquema al que se haga referencia en el atributo `xsd:schemaLocation`. Para obtener más información, consulte [validación de documentos XML](../xml-tools/xml-document-validation.md).  
  
### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Para seleccionar un esquema XML de la caché de esquema  
  
1. Abra un archivo en el Editor XML.  
  
2. En la ventana Propiedades del documento, haga clic en el botón en el **esquemas** campo.  
  
    El **esquemas XML** se muestra el cuadro de diálogo. El cuadro de diálogo enumera todos los esquemas con una extensión .xsd en la caché de esquema (incluidos los esquemas que se hace referenciados en el archivo catalog.xml), y también cualquier esquema al que se encuentra en la solución actual, abrir en Visual Studio, se hace referencia en un `xsd:schemaLocation` de atributo o hace referencia en el **esquemas** propiedad.  
  
3. Seleccione los esquemas que desea utilizar en la validación mediante una de las siguientes acciones:  
  
   - Seleccione un esquema que aparece en el **esquemas XML** cuadro de diálogo, haga clic en el **Use** columna y, a continuación, seleccione **utilizar este esquema**.  
  
     O bien  
  
   - Seleccione varios esquemas que aparecen en la **esquemas XML** cuadro de diálogo, con el botón secundario y seleccione **utilizar este esquema**.  
  
4. Haga clic en **Aceptar**.  
  
    La lista de esquemas seleccionados se copia en el **esquemas** propiedad de documento.  
  
### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Para agregar un esquema XML a la caché de esquema  
  
1.  En la ventana Propiedades del documento, haga clic en el botón en el **esquemas** campo.  
  
2.  Haga clic en **Agregar**.  
  
     Se abrirá el **Abrir esquema XSD** cuadro de diálogo.  
  
3.  Busque y seleccione los esquemas que se van a agregar a la caché de esquema.  
  
4.  Haga clic en **abierto**.  
  
     El esquema se agrega al esquema en caché y es el **Use** el valor de columna se establece en **utilizar este esquema**.  
  
### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Para eliminar un esquema XML de la caché de esquema  
  
1.  En la ventana Propiedades del documento, haga clic en el botón en el **esquemas** campo.  
  
2.  Seleccione el esquema para quitar y, a continuación, haga clic en **quitar**.  
  
     El esquema se quita de la caché de esquema en memoria, pero no del sistema de archivos.  
  
    > [!NOTE]
    >  Si todavía tiene una referencia al esquema a través de un `schemaLocation` atributo o una coincidencia con `targetNamespace` , a continuación, **quitar** no funcionarán en esta situación debido a la asociación automática. En este caso, se recomienda que marque el esquema como **no utilizar esquemas seleccionados** en el **usar** columna.  
  
## <a name="see-also"></a>Vea también  
 [Caché de esquema](../xml-tools/schema-cache.md)   
 [Cuadro de diálogo de esquemas XML](../xml-tools/xml-schemas-dialog-box.md)   
 [Editor XML](../xml-tools/xml-editor.md)



