---
title: 'Cómo: Crear un esquema XML a partir de un documento XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2f33fc5b48b9fd6b1cc08570e62e73f05fd19e70
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548310"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Cómo: crear un esquema XML a partir de un documento XML

El Editor XML permite crear un esquema de lenguaje de definición de esquemas XML (XSD) a partir de un documento XML. El documento de instancia XML determina cómo se genera el esquema de la siguiente manera:

-   Si el documento XML no tiene asociado un esquema o una definición de tipo de documento (DTD), los datos del documento XML se utilizan para inferir un nuevo esquema XML.

-   Si el documento XML contiene una DTD asociada, la DTD externa y el subconjunto interno se convierten en un esquema XML correspondiente.

-   Si el documento XML contiene un esquema reducido de datos XML (XDR) alineado, el esquema XDR se convierte en un esquema XML correspondiente.

Los esquemas creados se utilizan luego para proporcionar IntelliSense en el documento XML.

Para obtener más información acerca del motor de inferencia del esquema, consulte [deducir un esquema XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Para crear un esquema XML

1.  Cargue un documento de instancia XML en el Editor XML.

2.  Haga clic en el **Create Schema** botón desde la **barra de herramientas**.

     Se crea un documento de esquema XML, que se abre para cada espacio de nombres hallado en el documento de instancia XML. Cada esquema se abre como un archivo de varios temporal.

     Los esquemas se pueden guardar en un disco, agregarse a un proyecto o descartarse.

    > [!NOTE]
    >  El **Create Schema** comando también está disponible en el menú contextual del Editor XML y, en la **XML** menú.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)