---
title: "SccDiff (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccDiff"
helpviewer_keywords: 
  - "SccDiff (función)"
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# SccDiff (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función muestra \(o simplemente, opcionalmente, busca\) sistema de control de las diferencias entre el archivo actual \(en el disco local\) y la última versión protegida en el origen.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccDiff(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LPCSTR    lpFileName,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Parámetros  
 pvContext  
 \[in\] La estructura de contexto complemento de control de código fuente.  
  
 hWnd  
 \[in\] Identificador de la ventana del IDE que se puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 lpFileName  
 \[in\] Nombre de archivo para el que se solicita la diferencia.  
  
 Opciones  
 \[in\] Indicadores de comando. Para obtener más información, vea la sección Comentarios.  
  
 pvOptions  
 \[in\] Opciones específicas del complemento de control de código fuente.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|La versión de servidor y de copia de trabajo son idénticos.|  
|SCC\_I\_FILESDIFFERS|La copia de trabajo difiere de la versión bajo control de código fuente.|  
|SCC\_I\_RELOADFILE|Debe volver a cargar un archivo o proyecto.|  
|SCC\_E\_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|  
|SCC\_E\_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC\_E\_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de origen, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC\_E\_NONSPECIFICERROR|Error no específico; no se ha obtenido la diferencia del archivo.|  
|SCC\_E\_FILENOTEXIST|No se encontró el archivo local.|  
  
## Comentarios  
 Esta función sirve para dos propósitos diferentes. De forma predeterminada, muestra una lista de cambios en un archivo. El complemento de control de código fuente abre su propia ventana, en el mismo formato que elija, para mostrar las diferencias entre el archivo del usuario en el disco y la versión más reciente del archivo bajo control de código fuente.  
  
 Como alternativa, el IDE simplemente que necesite determinar si un archivo ha cambiado. Por ejemplo, el IDE necesite determinar si es seguro desproteger un archivo sin informar al usuario. En ese caso, el IDE se pasa en el `SCC_DIFF_CONTENTS` marca. El complemento de control de código fuente debe comprobar el archivo en disco, byte a byte en el archivo de control de código fuente y devolver un valor que indica si los dos archivos son diferentes sin mostrar nada al usuario.  
  
 Optimizar el rendimiento, el complemento de control de código fuente puede usar una alternativa basada en una suma de comprobación o una marca de tiempo en lugar de la comparación byte a byte llamada para `SCC_DIFF_CONTENTS`: estos formularios de comparación son obviamente más rápido pero menos confiable. No todos los sistemas de control de código fuente pueden admitir estos métodos alternativos de comparación y el complemento puede tener que recurrir a una comparación de contenido. Todos los complementos código fuente control deben, como mínimo, admite una comparación de contenido.  
  
> [!NOTE]
>  Las marcas de diferencia rápida son mutuamente excluyentes. Es válido para no pasar ningún marcador, pero no es válido para pasar simultáneamente más de uno.`SCC_DIFF_QUICK_DIFF`, que es una máscara que combina todas las marcas se pueden utilizar para probar, pero nunca se debería pasar como un parámetro.  
  
|`fOption`|Significado|  
|---------------|-----------------|  
|SCC\_DIFF\_IGNORECASE|Comparación entre mayúsculas y minúsculas \(se puede usar para diferencia rápido o visual\).|  
|SCC\_DIFF\_IGNORESPACE|Omite los espacios en blanco \(se puede usar para diferencia rápido o visual\).|  
|SCC\_DIFF\_QD\_CONTENTS|En modo silencioso, compara el archivo, byte a byte.|  
|SCC\_DIFF\_QD\_CHECKSUM|En modo silencioso, compara el archivo a través de una suma de comprobación cuando se admita. Si no se admite, recurre a una comparación de contenido.|  
|SCC\_DIFF\_QD\_TIME|En modo silencioso, compara el archivo a través de su marca de tiempo cuando se admita. Si no se admite, recurre a una comparación de contenido.|  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)