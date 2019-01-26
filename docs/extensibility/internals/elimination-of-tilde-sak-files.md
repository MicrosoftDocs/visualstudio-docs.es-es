---
title: Eliminación de ~ SAK archivos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 701bb929bae7b5103e274810cf0ad3a222118781
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951279"
---
# <a name="elimination-of-sak-files"></a>Eliminación de ~ archivos SAK
En fuente Control complemento API 1.2, el *~ SAK* archivos han sido reemplazados por marcadores de capacidad y nuevas funciones que detectan si un origen de controlan el complemento admite el *MSSCCPRJ* de archivos y las desprotecciones compartidas.  
  
## <a name="sak-files"></a>~ Archivos SAK  
Visual Studio .NET 2003 creó los archivos temporales con el prefijo *~ SAK*. Estos archivos se usan para determinar si un complemento de control de origen es compatible con:  
  
- El *MSSCCPRJ.SCC* archivo.  
  
- Varias desprotecciones (compartidas).  
    
Para los complementos que admiten las funciones avanzadas proporcionadas en la API de complemento de origen Control 1.2, el IDE puede detectar estas capacidades sin necesidad de crear los archivos temporales mediante el uso de nuevas funcionalidades, marcadores y las funciones, que se detallan en las secciones siguientes.  
  
## <a name="new-capability-flags"></a>Marcadores de capacidad nueva  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Nuevas funciones  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Si un complemento de control de origen admite varias desprotecciones (compartidas) y, después, declara el `SCC_CAP_MULTICHECKOUT` funcionalidad e implementa el `SccIsMultiCheckOutEnabled` función. Esta función se invoca siempre que se produzca una operación de desprotección en cualquiera de los proyectos controlados por código fuente.  
  
 Si un complemento de control de código fuente admite la creación y uso de un *MSSCCPRJ.SCC* de archivos, a continuación, declara el `SCC_CAP_SCCFILE` funcionalidad e implementa el [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Esta función se invoca con una lista de archivos. La función devuelve `TRUE' or 'FALSE` para cada archivo indicar si Visual Studio se debe utilizar un *MSSCCPRJ.SCC* archivo para él. Si elige el complemento de control de código fuente no admitir estas nuevas capacidades y funciones, puede usar la siguiente clave del registro para deshabilitar la creación de estos archivos:  
  
 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]DoNotCreateTemporaryFilesInSourceControl** = *dword:00000001*  
  
> [!NOTE]
>  Si se establece esta clave del registro en *DWORD: 00000000*, es equivalente a la clave es que no existe, y Visual Studio continúa realizando intentos para crear los archivos temporales. Sin embargo, si la clave del registro se establece en *DWORD: 00000001*, Visual Studio no intenta crear los archivos temporales. En su lugar, se supone que el complemento de control de origen no es compatible con la *MSSCCPRJ.SCC* de archivos y admitir desprotecciones compartidas.  
  
## <a name="see-also"></a>Vea también  
 [Novedades de la versión 1.2 de origen Control complemento de API](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)