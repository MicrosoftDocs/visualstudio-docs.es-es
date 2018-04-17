---
title: Eliminación de ~ SAK archivos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 61227652bf191280f69466f127c4a400ea43856e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="elimination-of-sak-files"></a>Eliminación de ~ SAK archivos
En origen Control complemento API 1.2, el ~ archivos SAK se reemplazaron por marcadores de capacidad y nuevas funciones que detectan si un complemento de control de origen es compatible con el archivo MSSCCPRJ y desprotecciones compartidas.  
  
## <a name="sak-files"></a>~ SAK archivos  
 Visual Studio .NET 2003 creado archivos temporales con el prefijo ~ SAK. Estos archivos se usan para determinar si es compatible con un complemento de control de código fuente:  
  
-   MSSCCPRJ. Archivo de control de código fuente.  
  
-   Varias desprotecciones (compartidas).  
  
 Para complementos que admiten funciones avanzadas proporcionadas en la 1.2 de API de complemento de Control origen, el IDE puede detectar estas funciones sin necesidad de crear los archivos temporales mediante el uso de nuevas funcionalidades, indicadores y funciones, que se detallan en las secciones siguientes.  
  
## <a name="new-capability-flags"></a>Nuevos indicadores de capacidad  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Nuevas funciones  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Si un complemento de control de origen admite varias desprotecciones (compartidas), a continuación, declara el `SCC_CAP_MULTICHECKOUT` capacidad e implementa el `SccIsMultiCheckOutEnabled` función. Esta función se invoca siempre que se produce una operación de desprotección en cualquiera de los proyectos controlados por código fuente.  
  
 Si un complemento de control de origen es compatible con la creación y uso de un MSSCCPRJ. Archivo de control de código fuente, a continuación, se declara el `SCC_CAP_SCCFILE` capacidad e implementa la [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Esta función se invoca con una lista de archivos. La función devuelve `TRUE/FALSE` para cada archivo indicar si Visual Studio debe usar un MSSCCPRJ. Archivo de control de código fuente para él. Si elige el complemento de control de código fuente no admitir estas nuevas capacidades y funciones, puede utilizar la siguiente clave del registro para deshabilitar la creación de estos archivos:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateTemporaryFilesInSourceControl" = dword: 00000001  
  
> [!NOTE]
>  Si esta clave del registro se establece en DWORD: 00000000, es equivalente a la clave que no existe, y continúa realizando intentos Visual Studio crear los archivos temporales. Sin embargo, si la clave del registro se establece en DWORD: 00000001, Visual Studio no intenta crear los archivos temporales. En su lugar, se supone que el complemento de control de origen no admite la MSSCCPRJ. Archivo de control de código fuente y admitir desprotecciones compartidas.  
  
## <a name="see-also"></a>Vea también  
 [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)