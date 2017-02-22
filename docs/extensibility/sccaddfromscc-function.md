---
title: "SccAddFromScc (funci&#243;n) | Microsoft Docs"
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
  - "SccAddFromScc"
helpviewer_keywords: 
  - "SccAddFromScc (función)"
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# SccAddFromScc (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función permite al usuario examinar archivos que ya están en el sistema de control de código fuente y posteriormente integrar esos archivos del proyecto actual. Por ejemplo, esta función puede obtener un archivo de encabezado común en el proyecto actual sin copiar el archivo. La matriz de devolución de archivos, `lplpFileNames`, contiene la lista de archivos que el usuario desea agregar al proyecto IDE.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
#### Parámetros  
 pvContext  
 \[in\] La estructura de contexto complemento de control de código fuente.  
  
 hWnd  
 \[in\] Identificador de la ventana del IDE que se puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 lpnFiles  
 \[entrada, salida\] Búfer para el número de archivos que se agregan. \(Esto es `NULL` Si la memoria indicada por `lplpFileNames` es que se libere. Vea la sección Comentarios para obtener más información\).  
  
 lplpFileNames  
 \[entrada, salida\] Una matriz de punteros a todos los nombres de archivo sin rutas de directorio. Esta matriz se asigna y libera el complemento de control de código fuente. Si `lpnFiles` \= 1 y `lplpFileNames` no `NULL`, señala el primer nombre de la matriz `lplpFileNames` contiene la carpeta de destino.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Los archivos se encuentra y se agrega al proyecto correctamente.|  
|SCC\_I\_OPERATIONCANCELED|Se canceló la operación sin efecto.|  
|SCC\_I\_RELOADFILE|Debe volver a cargar un archivo o proyecto.|  
  
## Comentarios  
 El IDE llama a esta función. Si el complemento de control de código fuente permite especificar una carpeta de destino local, el IDE pasa `lpnFiles` \= 1 y pasa el nombre de la carpeta local en `lplpFileNames`.  
  
 Cuando la llamada a la `SccAddFromScc` devuelve la función, el complemento se les asignan valores a `lpnFiles` y `lplpFileNames`, asignar la memoria para la matriz de nombre de archivo según sea necesario \(tenga en cuenta que esta asignación reemplaza el puntero en `lplpFileNames`\). El complemento de control de código fuente es responsable de colocar todos los archivos en el directorio del usuario o en la carpeta de designación especificado. El IDE, a continuación, agrega los archivos al proyecto del IDE.  
  
 Por último, el IDE llama a esta función una segunda vez, pasando `NULL` para `lpnFiles`. Esto se interpreta como una señal especial mediante el complemento para liberar la memoria asignada para la matriz de nombres de archivo en el control de código fuente `lplpFileNames``.`  
  
 `lplpFileNames` es un `char ***` puntero. El complemento de control de código fuente coloca un puntero a una matriz de punteros a los nombres de archivo, pasando así la lista de la forma estándar para esta API.  
  
> [!NOTE]
>  Las versiones iniciales de la API VSSCI no proporcionó una manera de indicar el proyecto de destino para los archivos agregados. Para permitir esto, la semántica de la `lplpFIleNames` parámetro que se han mejorado para que sea un parámetro de entrada y salida, en lugar de un parámetro de salida. Si sólo se especifica un solo archivo, es decir, el valor indicado por `lpnFiles` \= 1, entonces el primer elemento de `lplpFileNames` contiene la carpeta de destino. Para utilizar esta nueva semántica, las llamadas IDE la `SccSetOption` funciona con el `nOption`establecido en `SCC_OPT_SHARESUBPROJ`. Si un complemento de control de código fuente no admite la semántica, devuelve `SCC_E_OPTNOTSUPPORTED`. Hacer así deshabilita el uso de la **Agregar Control de código fuente** característica. Si un complemento admite el **Agregar Control de código fuente** característica \(`SCC_CAP_ADDFROMSCC`\), a continuación, debe admitir la nueva semántica y devolver `SCC_I_SHARESUBPROJOK`.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)