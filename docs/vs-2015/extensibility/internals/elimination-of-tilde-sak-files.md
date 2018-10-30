---
title: Eliminación de ~ SAK archivos | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7422b0dae02b12d731713f6da416361798d3276
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824316"
---
# <a name="elimination-of-sak-files"></a>Eliminación de archivos ~SAK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En fuente Control complemento API 1.2, el ~ archivos SAK han sido reemplazados por marcadores de capacidad y nuevas funciones que detectan si un complemento de control de origen es compatible con el archivo MSSCCPRJ y desprotecciones compartidas.  
  
## <a name="sak-files"></a>~ Archivos SAK  
 Visual Studio .NET 2003 creó los archivos temporales con el prefijo ~ SAK. Estos archivos se usan para determinar si un complemento de control de origen es compatible con:  
  
- El MSSCCPRJ. Archivo de control de código fuente.  
  
- Varias desprotecciones (compartidas).  
  
  Para los complementos que admiten las funciones avanzadas proporcionadas en la API de complemento de origen Control 1.2, el IDE puede detectar estas capacidades sin necesidad de crear los archivos temporales mediante el uso de nuevas funcionalidades, marcadores y las funciones, que se detallan en las secciones siguientes.  
  
## <a name="new-capability-flags"></a>Marcadores de capacidad nueva  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Nuevas funciones  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Si un complemento de control de origen admite varias desprotecciones (compartidas) y, después, declara el `SCC_CAP_MULTICHECKOUT` funcionalidad e implementa el `SccIsMultiCheckOutEnabled` función. Esta función se invoca siempre que se produzca una operación de desprotección en cualquiera de los proyectos controlados por código fuente.  
  
 Si un complemento de control de código fuente admite la creación y uso de un MSSCCPRJ. Archivo de control de código fuente, a continuación, se declara el `SCC_CAP_SCCFILE` funcionalidad e implementa el [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Esta función se invoca con una lista de archivos. La función devuelve `TRUE/FALSE` para cada archivo indicar si Visual Studio debe utilizar un MSSCCPRJ. Archivo de control de código fuente para él. Si elige el complemento de control de código fuente no admitir estas nuevas capacidades y funciones, puede usar la siguiente clave del registro para deshabilitar la creación de estos archivos:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateTemporaryFilesInSourceControl" = dword: 00000001  
  
> [!NOTE]
>  Si se establece esta clave del registro a DWORD: 00000000, es equivalente a la clave es que no existe, y Visual Studio continúa realizando intentos para crear los archivos temporales. Sin embargo, si se establece la clave del registro a DWORD: 00000001, Visual Studio no intenta crear los archivos temporales. En su lugar, se supone que el complemento de control de origen no es compatible con la MSSCCPRJ. Archivo de control de código fuente y admitir desprotecciones compartidas.  
  
## <a name="see-also"></a>Vea también  
 [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

