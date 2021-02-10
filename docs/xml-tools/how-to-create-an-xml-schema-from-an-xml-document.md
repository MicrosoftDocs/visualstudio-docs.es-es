---
title: Creación de un esquema XML
description: Aprenda a usar el editor XML de Visual Studio para crear un esquema de lenguaje de definición de esquema XML (XSD) a partir de un documento XML.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e33a4add7ebc6a3e323331731f3183d7a0dce26f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970288"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Procedimiento Creación de un esquema XML a partir de un documento XML

El editor XML permite crear un esquema de lenguaje de definición de esquemas XML (XSD) a partir de un documento XML. El archivo XML determina cómo se genera el esquema de la siguiente manera:

- Si el documento XML no tiene asociado un esquema o una definición de tipo de documento (DTD), los datos del documento XML se utilizan para inferir un nuevo esquema XML.

- Si el documento XML contiene una DTD asociada, la DTD externa y el subconjunto interno se convierten en un esquema XML correspondiente.

- Si el documento XML contiene un esquema reducido de datos XML (XDR) alineado, el esquema XDR se convierte en un esquema XML correspondiente.

Los esquemas creados se utilizan luego para proporcionar IntelliSense en el archivo XML.

Para más información sobre el motor de referencia de esquemas, vea [Deducción de esquema XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Para crear un esquema XML

1. Abra un archivo XML en Visual Studio.

2. En la barra de menús, elija **XML** > **Crear esquema**.

   Se crea un documento de esquema XML, que se abre para cada espacio de nombres hallado en el archivo XML. Cada esquema se abre como un archivo de varios temporal. Los esquemas se pueden guardar en un disco, agregarse a un proyecto o descartarse.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)
