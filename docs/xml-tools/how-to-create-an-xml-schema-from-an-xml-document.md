---
title: Crear un esquema XML
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 857b75f22d45cbabc22062fd14b385e8f6ea5f14
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592781"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Cómo: crear un esquema XML a partir de un documento XML

El editor XML permite crear un esquema del lenguaje de definición de esquemas XML (XSD) a partir de un documento XML. El archivo XML determina cómo se genera el esquema de la siguiente manera:

- Si el documento XML no tiene asociado un esquema o una definición de tipo de documento (DTD), los datos del documento XML se utilizan para inferir un nuevo esquema XML.

- Si el documento XML contiene una DTD asociada, la DTD externa y el subconjunto interno se convierten en un esquema XML correspondiente.

- Si el documento XML contiene un esquema reducido de datos XML (XDR) alineado, el esquema XDR se convierte en un esquema XML correspondiente.

Los esquemas que se crean se utilizan para proporcionar IntelliSense para el archivo XML.

Para obtener más información sobre el motor de inferencia de esquema, vea [inferir un esquema XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Para crear un esquema XML

1. Abra un archivo XML en Visual Studio.

2. En la barra de menús, elija **XML** > **crear esquema**.

   Se crea y se abre un documento de esquema XML para cada espacio de nombres que se encuentra en el archivo XML. Cada esquema se abre como un archivo de varios temporal. Los esquemas se pueden guardar en un disco, agregarse a un proyecto o descartarse.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)
