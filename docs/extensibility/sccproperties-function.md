---
title: Función SccProperties (SccProperties) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf2dd87efbb50346093144db6e069eea30138e37
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700505"
---
# <a name="sccproperties-function"></a>SccProperties (Función)
Esta función muestra las propiedades de control de código fuente para un archivo o proyecto.

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

[en] La estructura de contexto del complemento de control de código fuente.

 hWnd

[en] Identificador de la ventana IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 lpFileName

[en] El nombre de ruta de acceso completo del archivo o proyecto.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|Las propiedades se mostraron correctamente.|
|SCC_I_RELOADFILE|El sistema de control de versiones ha modificado las propiedades del archivo, por lo que el IDE debe volver a cargar este archivo.|
|SCC_E_PROJNOTOPEN|El proyecto especificado no se ha abierto en el control de código fuente.|
|SCC_E_NOTAUTHORIZED|El usuario no está autorizado para ver las propiedades de este archivo o proyecto.|
|SCC_E_FILENOTCONTROLLED|El archivo o proyecto especificado no está bajo control de código fuente.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Se ha producido un error desconocido o general.|

## <a name="remarks"></a>Observaciones
 El complemento de control de código fuente muestra las propiedades en su propio cuadro de diálogo.

 Las propiedades se definen mediante el complemento de control de código fuente y pueden diferir de un complemento a un complemento. Si el complemento permite al usuario cambiar las propiedades de control `SCC_I_RELOAD` de código fuente de un archivo, debe volver a indicar al IDE que este archivo o proyecto debe volver a cargarse.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
