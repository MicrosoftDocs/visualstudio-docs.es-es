---
title: Validación de documentos XML en el Editor XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 389328e97f29d97962353e86f73c39c7c5459bfc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592417"
---
# <a name="xml-document-validation"></a>Validación de documentos XML

El Editor XML comprueba la sintaxis XML 1.0 y también realiza la validación de los datos mientras escribe. Para realizar la validación, el editor utiliza una definición de tipo de documento (DTD) o un esquema. Un subrayado ondulado rojo resalta los errores de XML 1.0 con un formato correcto. Un subrayado ondulado azul muestra errores semánticos basados en la validación de DTD o de esquemas. Cada error posee una entrada asociada en la lista de errores. También puede ver el mensaje de error si detiene el mouse sobre el subrayado ondulado.

Para encontrar los esquemas usados en la validación se hace coincidir el `targetNamespace` de un esquema compilado con la declaración xmlns del elemento. Los esquemas compilados se cargan desde una de las siguientes ubicaciones, mostradas en orden de prioridad:

- Desde el nombre de archivo especificado en el campo **Esquemas** de la ventana **Propiedades** del documento.

- Un esquema o DTD alineado.

- Una DTD externa o un atributo `xsd:schemaLocation` y `xsd:noNamespaceSchemaLocation`

- Un identificador URI de espacio de nombres de esquema XDR "x-schema".

También es posible encontrar esquemas en estos otros lugares cuando el esquema tiene un espacio de nombres de destino que no está vacío:

- Otra ventana del editor que contiene el esquema.

- Un esquema de la solución actual.

- Un esquema del directorio de la caché de esquema.

## <a name="xslt-files"></a>Archivos XSLT
Al editar un archivo XSLT, se utiliza en la validación el archivo *xslt.xsd* ubicado en la caché de esquemas. Los errores de validación se muestran con un subrayado ondulado de color azul. Los errores del compilador XSLT se muestran con un subrayado ondulado rojo.

## <a name="xml-schema-xsd-files"></a>Archivos de esquema XML (XSD)
Al editar un archivo de esquema XML, se utiliza en la validación el archivo *xsdschema.xsd* ubicado en la caché de esquemas. Los errores de validación se muestran con un subrayado ondulado de color azul. Los errores de compilación también se muestra con un subrayado ondulado rojo.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)
