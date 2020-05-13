---
title: Eliminación de los archivos de la página de la ciudad de SAK Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708498"
---
# <a name="elimination-of-sak-files"></a>Eliminación de los archivos de la aplicación de la aplicación de la aplicación de la aplicación
En la API de complemento de control de código fuente 1.2, los archivos *de* la aplicación se han reemplazado por indicadores de capacidad y nuevas funciones que detectan si un complemento de control de código fuente admite el archivo *MSSCCPRJ* y las desprotecciones compartidas.

## <a name="sak-files"></a>Archivos de la página de trabajo
Visual Studio .NET 2003 creó archivos temporales con el prefijo *.SAK*. Estos archivos se utilizan para determinar si un complemento de control de código fuente admite:

- El archivo *MSSCCPRJ.SCC.*

- Múltiples desprotecciones (compartidas).

Para los complementos que admiten funciones avanzadas proporcionadas en la API de complemento de Control de código fuente 1.2, el IDE puede detectar estas capacidades sin crear los archivos temporales mediante el uso de nuevas capacidades, indicadores y funciones, que se detallan en las secciones siguientes.

## <a name="new-capability-flags"></a>Nuevos indicadores de capacidad
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>Nuevas funciones
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 Si un complemento de control de código fuente admite varias `SCC_CAP_MULTICHECKOUT` desprotecciones `SccIsMultiCheckOutEnabled` (compartidas), declara la capacidad e implementa la función. Esta función se llama siempre que se produce una operación de desprotección en cualquiera de los proyectos controlados por código fuente.

 Si un complemento de control de código fuente admite la creación y el uso de `SCC_CAP_SCCFILE` un archivo *MSSCCPRJ.SCC,* declara la capacidad e implementa [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Esta función se llama con una lista de archivos. La función devuelve `TRUE' or 'FALSE` para cada archivo para indicar si Visual Studio debe usar un archivo *MSSCCPRJ.SCC* para él. Si el complemento de control de código fuente decide no admitir estas nuevas capacidades y funciones, puede usar la siguiente clave del Registro para deshabilitar la creación de estos archivos:

 **[HKEY_CURRENT_USER,Software, Microsoft, VisualStudio, 8.0, SourceControl] DoNotCreateTemporaryFilesInSourceControl** = *dword:00000001*

> [!NOTE]
> Si esta clave del Registro se establece en *dword:00000000*, equivale a que la clave no existe y Visual Studio sigue intentando crear los archivos temporales. Sin embargo, si la clave del Registro se establece en *dword:00000001*, Visual Studio no intenta crear los archivos temporales. En su lugar, se supone que el complemento de control de código fuente no admite el archivo *MSSCCPRJ.SCC* y no admite desprotecciones compartidas.

## <a name="see-also"></a>Vea también
- [Novedades de la API de complemento de Control de código fuente versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
