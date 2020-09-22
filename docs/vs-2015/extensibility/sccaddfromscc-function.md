---
title: Función SccAddFromScc | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ccf3a25bda14cf98fdba4a58b0032444badc4c4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842983"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función permite al usuario buscar archivos que ya están en el sistema de control de código fuente y, posteriormente, hacer que dichos archivos formen parte del proyecto actual. Por ejemplo, esta función puede obtener un archivo de encabezado común en el proyecto actual sin copiar el archivo. La matriz devuelta de archivos, `lplpFileNames` , contiene la lista de archivos que el usuario desea agregar al proyecto IDE.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pvContext  
 de Estructura de contexto del complemento de control de código fuente.  
  
 hWnd  
 de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.  
  
 lpnFiles  
 [in, out] Búfer para el número de archivos que se van a agregar a. (Es si se va `NULL` a liberar la memoria a la que apunta `lplpFileNames` . Vea la sección Comentarios para obtener más información).  
  
 lplpFileNames  
 [in, out] Matriz de punteros a todos los nombres de archivo sin rutas de acceso de directorio. El complemento de control de código fuente asigna y libera esta matriz. Si `lpnFiles` = 1 y `lplpFileNames` no es `NULL` , el primer nombre de la matriz a la que apunta `lplpFileNames` contiene la carpeta de destino.  
  
## <a name="return-value"></a>Valor devuelto  
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:  
  
|Value|Descripción|  
|-----------|-----------------|  
|SCC_OK|Los archivos se han encontrado y agregado correctamente al proyecto.|  
|SCC_I_OPERATIONCANCELED|La operación se canceló sin ningún efecto.|  
|SCC_I_RELOADFILE|Es necesario volver a cargar un archivo o proyecto.|  
  
## <a name="remarks"></a>Notas  
 El IDE llama a esta función. Si el complemento de control de código fuente admite la especificación de una carpeta de destino local, el IDE pasa `lpnFiles` = 1 y pasa el nombre de la carpeta local a `lplpFileNames` .  
  
 Cuando se devuelve la llamada a la `SccAddFromScc` función, el complemento tiene asignados valores a `lpnFiles` y `lplpFileNames` , asignando la memoria para la matriz de nombres de archivo según sea necesario (tenga en cuenta que esta asignación reemplaza el puntero en `lplpFileNames` ). El complemento de control de código fuente es responsable de colocar todos los archivos en el directorio del usuario o en la carpeta designada. A continuación, el IDE agrega los archivos al proyecto IDE.  
  
 Por último, el IDE llama a esta función por segunda vez, pasando `NULL` para `lpnFiles` . El complemento de control de código fuente interpreta esto como una señal especial para liberar la memoria asignada para la matriz de nombres de archivo en `lplpFileNames``.`  
  
 `lplpFileNames` es un `char ***` puntero. El complemento de control de código fuente coloca un puntero a una matriz de punteros a nombres de archivo, con lo que se pasa la lista de la manera estándar para esta API.  
  
> [!NOTE]
> Las versiones iniciales de la API de VSSCI no proporcionaban una manera de indicar el proyecto de destino para los archivos agregados. Para dar cabida a esto, se ha mejorado la semántica del `lplpFIleNames` parámetro para convertirlo en un parámetro in/out en lugar de un parámetro de salida. Si solo se especifica un archivo, es decir, el valor al que apunta `lpnFiles` = 1, el primer elemento de `lplpFileNames` contiene la carpeta de destino. Para usar estas nuevas semánticas, el IDE llama `SccSetOption` a la función con el `nOption` parámetro establecido en `SCC_OPT_SHARESUBPROJ` . Si un complemento de control de código fuente no admite la semántica, devuelve `SCC_E_OPTNOTSUPPORTED` . Al hacerlo, se deshabilita el uso de la característica **Agregar desde el control de código fuente** . Si un complemento admite la característica **Agregar de control de código fuente** ( `SCC_CAP_ADDFROMSCC` ), debe admitir la nueva semántica y devolver `SCC_I_SHARESUBPROJOK` .  
  
## <a name="see-also"></a>Consulte también  
 [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)
