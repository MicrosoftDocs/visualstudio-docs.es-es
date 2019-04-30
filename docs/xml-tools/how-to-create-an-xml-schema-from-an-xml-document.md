---
title: Crear un esquema XML
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e93155f230ee4a564116f5d1357a97923706c36
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783498"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Procedimiento Creación de un esquema XML a partir de un documento XML

El editor XML permite crear un esquema (XSD) del lenguaje de definición de esquemas XML de un documento XML. El archivo XML determina cómo se genera el esquema de la siguiente manera:

- Si el documento XML no tiene asociado un esquema o una definición de tipo de documento (DTD), los datos del documento XML se utilizan para inferir un nuevo esquema XML.

- Si el documento XML contiene una DTD asociada, la DTD externa y el subconjunto interno se convierten en un esquema XML correspondiente.

- Si el documento XML contiene un esquema reducido de datos XML (XDR) alineado, el esquema XDR se convierte en un esquema XML correspondiente.

Los esquemas que se crean, a continuación, se usan para proporcionar IntelliSense para el archivo XML.

Para obtener más información acerca del motor de inferencia del esquema, vea [inferir un esquema XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Para crear un esquema XML

1. Abra un archivo XML en Visual Studio.

2. En la barra de menús, elija **XML** > **Create Schema**.

   Se crea un documento de esquema XML y se abre para cada espacio de nombres que se encuentra en el archivo XML. Cada esquema se abre como un archivo de varios temporal. Los esquemas se pueden guardar en un disco, agregarse a un proyecto o descartarse.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)