---
title: Eliminación de archivos ~ SAK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 751acf4e5f56b7b477f05ab71571e0becd566649
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842511"
---
# <a name="elimination-of-sak-files"></a>Eliminación de archivos ~SAK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En la API 1,2 del complemento de control de código fuente, los archivos ~ SAK se han reemplazado por marcas de funcionalidad y nuevas funciones que detectan si un complemento de control de código fuente admite el archivo MSSCCPRJ y las desprotecciones compartidas.  
  
## <a name="sak-files"></a>Archivos ~ SAK  
 Visual Studio .NET 2003 creó archivos temporales prefijados con ~ SAK. Estos archivos se usan para determinar si un complemento de control de código fuente admite:  
  
- MSSCCPRJ. Archivo SCC.  
  
- Varias desprotecciones (compartidas).  
  
  En el caso de los complementos que admiten funciones avanzadas proporcionadas en la API de complemento de control de código fuente 1,2, el IDE puede detectar estas capacidades sin crear los archivos temporales mediante el uso de nuevas capacidades, marcas y funciones, que se detallan en las secciones siguientes.  
  
## <a name="new-capability-flags"></a>Nuevas marcas de capacidad  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Funciones nuevas  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Si un complemento de control de código fuente admite varias desprotecciones (compartidas), declara la `SCC_CAP_MULTICHECKOUT` funcionalidad e implementa la `SccIsMultiCheckOutEnabled` función. Se llama a esta función siempre que se produce una operación de desprotección en cualquiera de los proyectos controlados por código fuente.  
  
 Si un complemento de control de código fuente admite la creación y el uso de una MSSCCPRJ. SCC, después declara la `SCC_CAP_SCCFILE` funcionalidad e implementa [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Se llama a esta función con una lista de archivos. La función devuelve `TRUE/FALSE` para cada archivo para indicar si Visual Studio debe usar MSSCCPRJ. Archivo SCC para él. Si el complemento de control de código fuente opta por no admitir estas nuevas funciones y funciones, puede usar la siguiente clave del registro para deshabilitar la creación de estos archivos:  
  
 [HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateTemporaryFilesInSourceControl" = dword: 00000001  
  
> [!NOTE]
> Si esta clave del registro se establece en DWORD: 00000000, es equivalente a la clave que no existe y Visual Studio sigue intentando crear los archivos temporales. Sin embargo, si la clave del registro se establece en DWORD: 00000001, Visual Studio no intenta crear los archivos temporales. En su lugar, se supone que el complemento de control de código fuente no admite MSSCCPRJ. El archivo SCC y no admite desprotecciones compartidas.  
  
## <a name="see-also"></a>Consulte también  
 [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
