---
title: Procedimiento Crear un esquema XML a partir de un documento XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32072a25a57988c0cf1273518e5c0a5d4745fe20
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033809"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Procedimiento Crear un esquema XML de un documento XML

El Editor XML permite crear un esquema de lenguaje de definición de esquemas XML (XSD) a partir de un documento XML. El documento de instancia XML determina cómo se genera el esquema de la siguiente manera:

-   Si el documento XML no tiene asociado un esquema o una definición de tipo de documento (DTD), los datos del documento XML se utilizan para inferir un nuevo esquema XML.

-   Si el documento XML contiene una DTD asociada, la DTD externa y el subconjunto interno se convierten en un esquema XML correspondiente.

-   Si el documento XML contiene un esquema reducido de datos XML (XDR) alineado, el esquema XDR se convierte en un esquema XML correspondiente.

Los esquemas creados se utilizan luego para proporcionar IntelliSense en el documento XML.

Para obtener más información acerca del motor de inferencia del esquema, vea [deducción de esquema XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Para crear un esquema XML

1.  Cargue un documento de instancia XML en el Editor XML.

2.  Haga clic en el **Create Schema** botón desde la **barra de herramientas**.

     Se crea un documento de esquema XML, que se abre para cada espacio de nombres hallado en el documento de instancia XML. Cada esquema se abre como un archivo de varios temporal.

     Los esquemas se pueden guardar en un disco, agregarse a un proyecto o descartarse.

    > [!NOTE]
    >  El **Create Schema** comando también está disponible en el menú contextual del Editor XML y, en el **XML** menú.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)