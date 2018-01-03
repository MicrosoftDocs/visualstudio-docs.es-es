---
title: MarK | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8fb616cd9b938bb2624d762272f98ae2ad1f7fe9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="mark"></a>Marca
La opción **MarK** (marca) de VSPerfCmd.exe inserta la información especificada en el archivo de datos de generación de perfiles. La marca puede incluirse en un informe de VSPerfReport independiente o en la vista de informe de marca de la interfaz de usuario del generador de perfiles. **Mark** se puede usar para especificar los puntos inicial y final en los filtros de informe y vista.  
  
 La opción **Mark** debe ser la única especificada en la línea de comandos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `MarkID`  
 Entero definido por el usuario que aparece como el identificador de marca en los informes y vistas de generador de perfiles. `MarkID` no tiene que ser único.  
  
 `MarkName`  
 (Opcional) Cadena definida por el usuario que aparece como el nombre de la marca en los informes y vistas de generador de perfiles. Si `MarkName` no se especifica, el campo de nombre de la marca aparecerá vacío. Entrecomille las cadenas que contengan espacios o barras diagonales ("/").  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se inserta una marca con un identificador "123" y el nombre de marca "TestMark".  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)