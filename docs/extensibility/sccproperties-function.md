---
title: "SccProperties (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccProperties"
helpviewer_keywords: 
  - "SccProperties (función)"
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# SccProperties (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función muestra propiedades de control de código fuente para un archivo o proyecto.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### Parámetros  
 pvContext  
 \[in\] La estructura de contexto complemento de control de código fuente.  
  
 hWnd  
 \[in\] Identificador de la ventana del IDE que se puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 lpFileName  
 \[in\] El nombre de ruta de acceso completa del archivo o proyecto.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Las propiedades se muestran correctamente.|  
|SCC\_I\_RELOADFILE|El sistema de control de versiones modificó las propiedades del archivo, por lo que el IDE debe cargar este archivo.|  
|SCC\_E\_PROJNOTOPEN|No se abrió el proyecto especificado en el control de código fuente.|  
|SCC\_E\_NOTAUTHORIZED|El usuario no está autorizado para ver las propiedades de este archivo o proyecto.|  
|SCC\_E\_FILENOTCONTROLLED|El archivo especificado o el proyecto no está bajo control de código fuente.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Se produjo un error desconocido o general.|  
  
## Comentarios  
 El complemento de control de código fuente muestra las propiedades en su propio cuadro de diálogo.  
  
 Las propiedades se definen mediante el complemento de control de código fuente y pueden diferir de complemento para el complemento. Si el complemento permite al usuario cambiar las propiedades del control de origen de un archivo, debe devolver `SCC_I_RELOAD` para señalar el IDE que necesite volver a cargar este archivo o proyecto.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)