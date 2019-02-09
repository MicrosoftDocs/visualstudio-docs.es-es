---
title: Validación de documentos XML en el Editor XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74c8f327f17e6d2e05d0748195cb139f3a05a6f4
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931200"
---
# <a name="xml-document-validation"></a>Validación de documentos XML

El Editor XML comprueba la sintaxis XML 1.0 y realiza la validación de los datos mientras escribe. Para realizar la validación, el editor utiliza una definición de tipo de documento (DTD) o un esquema. Un subrayado ondulado rojo resalta los errores de XML 1.0 con un formato correcto. Un subrayado ondulado azul muestra errores semánticos basados en la validación de DTD o de esquemas. Cada error posee una entrada asociada en la lista de errores. También puede ver el mensaje de error si detiene el mouse sobre el subrayado ondulado.

 Para encontrar los esquemas usados en la validación se hace coincidir el `targetNamespace` de un esquema compilado con la declaración xmlns del elemento. Los esquemas compilados se cargan desde una de las siguientes ubicaciones, mostradas en orden de prioridad:

-   El nombre de archivo especificado en el **esquemas** campo del documento **propiedades** ventana.

-   Un esquema o DTD alineado.

-   Una DTD externa o un atributo `xsd:schemaLocation` y `xsd:noNamespaceSchemaLocation`

-   Un identificador URI de espacio de nombres de esquema XDR "x-schema".

También es posible encontrar esquemas en estos otros lugares cuando el esquema tiene un espacio de nombres de destino que no está vacío:

-   Otra ventana del editor que contiene el esquema.

-   Un esquema de la solución actual.

-   Un esquema del directorio de la caché de esquema.

## <a name="xslt-files"></a>Archivos XSLT
 Al editar un archivo XSLT, el *xslt.xsd* archivo se encuentra en la caché de esquema se utiliza para la validación. Los errores de validación se muestran con un subrayado ondulado de color azul. Los errores del compilador XSLT se muestran con un subrayado ondulado rojo.

## <a name="xml-schema-xsd-files"></a>Archivos de esquema (XSD) XML
 Al editar un archivo de esquema XML, el *xsdschema.xsd* archivo se encuentra en la caché de esquema se utiliza para la validación. Los errores de validación se muestran con un subrayado ondulado de color azul. Los errores de compilación también se muestra con un subrayado ondulado rojo.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)