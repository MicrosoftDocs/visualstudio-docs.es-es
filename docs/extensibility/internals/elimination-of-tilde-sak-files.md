---
title: Eliminación de archivos ~ SAK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0294198bb1560f8df6f17170013f88d4fe11e5cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708498"
---
# <a name="elimination-of-sak-files"></a>Eliminación de archivos ~ SAK
En la API 1,2 del complemento de control de código fuente, los archivos *~ Sak* se han reemplazado por marcas de funcionalidad y nuevas funciones que detectan si un complemento de control de código fuente admite el archivo *MSSCCPRJ* y las desprotecciones compartidas.

## <a name="sak-files"></a>Archivos ~ SAK
Visual Studio .NET 2003 creó archivos temporales prefijados con *~ Sak*. Estos archivos se usan para determinar si un complemento de control de código fuente admite:

- El archivo *MSSCCPRJ. SCC* .

- Varias desprotecciones (compartidas).

En el caso de los complementos que admiten funciones avanzadas proporcionadas en la API de complemento de control de código fuente 1,2, el IDE puede detectar estas capacidades sin crear los archivos temporales mediante el uso de nuevas capacidades, marcas y funciones, que se detallan en las secciones siguientes.

## <a name="new-capability-flags"></a>Nuevas marcas de capacidad
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>Nuevas funciones
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 Si un complemento de control de código fuente admite varias desprotecciones (compartidas), declara la `SCC_CAP_MULTICHECKOUT` funcionalidad e implementa la `SccIsMultiCheckOutEnabled` función. Se llama a esta función siempre que se produce una operación de desprotección en cualquiera de los proyectos controlados por código fuente.

 Si un complemento de control de código fuente admite la creación y el uso de un archivo *MSSCCPRJ. SCC* , declara la `SCC_CAP_SCCFILE` funcionalidad e implementa [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Se llama a esta función con una lista de archivos. La función devuelve `TRUE' or 'FALSE` para cada archivo para indicar si Visual Studio debe utilizar un archivo *MSSCCPRJ. SCC* para él. Si el complemento de control de código fuente opta por no admitir estas nuevas funciones y funciones, puede usar la siguiente clave del registro para deshabilitar la creación de estos archivos:

 **[HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0\sourcecontrol] DoNotCreateTemporaryFilesInSourceControl**  =  *DWORD: 00000001*

> [!NOTE]
> Si esta clave del registro se establece en *DWORD: 00000000*, es equivalente a la clave que no existe y Visual Studio sigue intentando crear los archivos temporales. Sin embargo, si la clave del registro se establece en *DWORD: 00000001*, Visual Studio no intenta crear los archivos temporales. En su lugar, supone que el complemento de control de código fuente no admite el archivo *MSSCCPRJ. SCC* y no admite desprotecciones compartidas.

## <a name="see-also"></a>Consulte también
- [Novedades de la API del complemento de control de código fuente versión 1,2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
