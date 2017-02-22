---
title: "CvCreateMarkerSeriesWithCodePageA (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmakers/CvCreateMarkerSeriesWithCodePageA"
helpviewer_keywords: 
  - "CvCreateMarkerSeriesWithCodePageA (método)"
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvCreateMarkerSeriesWithCodePageA (Funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Crea series de marcadores para un proveedor dado y una página de códigos especificados.  Esta función se puede utilizar para especificar la página de códigos explícitamente para el texto escrito por las funciones de la API ANSI del marcador.  Establecer la página de códigos puede ser útil en caso de que el seguimiento sea capturado y luego analizado en equipos diferentes con las diferentes configuraciones regionales y lenguajes.  De forma predeterminada, se utiliza la página de códigos devuelta por la función de GetACP\(\).  
  
## Sintaxis  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### Parámetros  
 `pProvider`  
 El objeto proveedor inicializado previamente por CvInitProvider.  No puede ser NULL.  
  
 `pSeriesName`  
 Nombre de la serie del marcador.  No puede ser NULL pero se permite la cadena vacía.  
  
 `nTextCodePage`  
 Página de códigos válida  
  
 `ppMarkerSeries`  
 Dirección de una variable de salida que almacenará contexto de la serie de marcadores.  No puede ser NULL.  
  
## Valor devuelto  
 S\_OK cuando la serie de marcadores se crea correctamente o se lanza un código de error en caso de cualquier error.  Utilizar macros SUCCEEDED\/FAILED para comprobar si hay condición de error.  
  
## Requisitos  
 **Encabezado:** cvmarkers.h  
  
## Vea también  
 [Referencia de la biblioteca C\+\+](../profiling/cpp-library-reference.md)