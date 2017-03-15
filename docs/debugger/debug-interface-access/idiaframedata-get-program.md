---
title: "IDiaFrameData::get_program | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaFrameData::get_program (método)"
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaFrameData::get_program
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera la cadena del programa se utiliza para calcular el conjunto de registros antes de la llamada a la función actual.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  Devuelve la cadena del programa.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si esta propiedad no se admite.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 La cadena de programa es una secuencia de macros que se interpreta para establecer el prólogo.  Por ejemplo, un marco de pila típico podría utilizar la cadena `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`del programa.  El formato es la notación polaca inversa, donde los operadores sigan los operandos.  `T0` representa una variable temporal en la pila.  Este ejemplo realiza los pasos siguientes:  
  
1.  Contenido de mover el registro `ebp` a `T0`.  
  
2.  Agregue `4` al valor en `T0` para generar una dirección, obtenga el valor de esa dirección, y almacenar el valor en el registro `eip`.  
  
3.  Obtenga el valor de la dirección almacenada en `T0` y almacena el valor en el registro `ebp`.  
  
4.  Agregue `8` al valor en `T0` y almacena el valor en el registro `esp`.  
  
 Observe que la cadena del programa es específica de la CPU y la configuración de la convención de llamada de la función representada por el marco de pila actual.  
  
## Vea también  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)