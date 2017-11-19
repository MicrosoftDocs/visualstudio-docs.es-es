---
title: Clase VsgDbg | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0ee36596521f26ff4dd948e697640d0c82d796f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="vsgdbg-class"></a>VsgDbg (Clase)
Representa una interfaz para el control mediante programación del componente de aplicación de diagnóstico de gráficos.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
class VsgDbg;  
```  
  
## <a name="members"></a>Miembros  
 La clase `VsgDbg` admite los miembros siguientes.  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (Constructor)](vsgdbg-vsgdbg-constructor.md)|Construye una instancia de la clase `VsgDbg` y prepara opcionalmente el componente de aplicación de diagnóstico de gráficos para capturar y grabar activamente información de gráficos.|  
|[VsgDbg::~VsgDbg (Destructor)](vsgdbg-tilde-vsgdbg-destructor.md)|Destruye una instancia de la clase `VsgDbg`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[AddMessage](addmessage.md)|Agrega un mensaje personalizado al HUD (pantalla de visualización frontal) de diagnóstico de gráficos.|  
|[BeginCapture](begincapture.md)|Inicia un intervalo de captura que finalizará con `EndCapture`.|  
|[CaptureCurrentFrame](capturecurrentframe.md)|Captura el resto del fotograma actual en el archivo de registro de gráficos.|  
|[Copiar (captura mediante programación)](copy-programmatic-capture.md)|Copia el contenido del archivo de registro de gráficos (.vsglog) activo en un nuevo archivo.|  
|[EndCapture](endcapture.md)|Finaliza un intervalo de captura que se inició con `BeginCapture`.|  
|[Init](init.md)|Prepara el componente de aplicación de diagnóstico de gráficos para capturar y grabar activamente información de gráficos.|  
|[ToggleHUD](togglehud.md)|Alterna la activación o desactivación de la superposición del HUD de diagnóstico de gráficos.|  
|[UnInit](uninit.md)|Finaliza el archivo de registro de gráficos, lo cierra y libera los recursos utilizados mientras la aplicación estaba grabando activamente información de gráficos.|  
  
## <a name="remarks"></a>Comentarios  
 La clase `VsgDbg` representa una interfaz que puede utilizar para controlar las características de diagnóstico de gráficos mediante programación. Puede utilizar algunas características incluso cuando no está capturando y registrando información de gráficos activamente; esto incluye las funciones miembro `AddMessage` y `ToggleHUD`. Las demás funciones miembro preparan el componente de aplicación de diagnóstico de gráficos para iniciar o detener la captura activa de información de gráficos, o se deben llamar mientras la aplicación está capturando y registrando información de gráficos en un archivo de registro de gráficos de forma activa.