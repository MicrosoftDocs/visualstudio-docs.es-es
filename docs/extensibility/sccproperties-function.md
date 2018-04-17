---
title: Función SccProperties | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1d126a4691332f1121ebfc99a84b180d1e99f3d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="sccproperties-function"></a>SccProperties (función)
Esta función muestra las propiedades de control de origen para un archivo o proyecto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pvContext  
 [in] La estructura de contexto de complemento de control de código fuente.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 lpFileName  
 [in] El nombre de ruta de acceso completa del archivo o proyecto.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Las propiedades se muestran correctamente.|  
|SCC_I_RELOADFILE|El sistema de control de versiones modificó las propiedades del archivo, por lo que el IDE debe volver a cargar este archivo.|  
|SCC_E_PROJNOTOPEN|No se ha abierto el proyecto especificado en el control de código fuente.|  
|SCC_E_NOTAUTHORIZED|El usuario no está autorizado para ver las propiedades de este archivo o proyecto.|  
|SCC_E_FILENOTCONTROLLED|El archivo especificado o el proyecto no está bajo control de código fuente.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Se produjo un error desconocido o general.|  
  
## <a name="remarks"></a>Comentarios  
 El complemento de control de código fuente muestra las propiedades en su propio cuadro de diálogo.  
  
 Las propiedades se definen mediante el complemento de control de código fuente y pueden diferir del complemento al complemento. Si el complemento permite al usuario cambiar las propiedades de control de código fuente de un archivo, debe devolver `SCC_I_RELOAD` para señalar el IDE que necesite volver a cargar este archivo o proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)