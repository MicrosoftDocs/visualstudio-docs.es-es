---
title: VsgDbg (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f83f3060764df37411477333a92f04648d66204f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193100"
---
# <a name="vsgdbg-class"></a>VsgDbg (Clase)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Representa una interfaz para el control mediante programación del componente de aplicación de diagnóstico de gráficos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
class VsgDbg;  
```  
  
## <a name="members"></a>Miembros  
 La clase `VsgDbg` admite los miembros siguientes.  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (Constructor)](../debugger/vsgdbg-vsgdbg-constructor.md)|Construye una instancia de la clase `VsgDbg` y prepara opcionalmente el componente de aplicación de diagnóstico de gráficos para capturar y grabar activamente información de gráficos.|  
|[VsgDbg::~VsgDbg (Destructor)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|Destruye una instancia de la clase `VsgDbg`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[AddMessage](../debugger/addmessage.md)|Agrega un mensaje personalizado al HUD (pantalla de visualización frontal) de diagnóstico de gráficos.|  
|[BeginCapture](../debugger/begincapture.md)|Inicia un intervalo de captura que finalizará con `EndCapture`.|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|Captura el resto del fotograma actual en el archivo de registro de gráficos.|  
|[Copiar (captura mediante programación)](../debugger/copy-programmatic-capture.md)|Copia el contenido del archivo de registro de gráficos (.vsglog) activo en un nuevo archivo.|  
|[EndCapture](../debugger/endcapture.md)|Finaliza un intervalo de captura que se inició con `BeginCapture`.|  
|[Init](../debugger/init.md)|Prepara el componente de aplicación de diagnóstico de gráficos para capturar y grabar activamente información de gráficos.|  
|[ToggleHUD](../debugger/togglehud.md)|Alterna la activación o desactivación de la superposición del HUD de diagnóstico de gráficos.|  
|[UnInit](../debugger/uninit.md)|Finaliza el archivo de registro de gráficos, lo cierra y libera los recursos utilizados mientras la aplicación estaba grabando activamente información de gráficos.|  
  
## <a name="remarks"></a>Comentarios  
 La clase `VsgDbg` representa una interfaz que puede utilizar para controlar las características de diagnóstico de gráficos mediante programación. Puede utilizar algunas características incluso cuando no está capturando y registrando información de gráficos activamente; esto incluye las funciones miembro `AddMessage` y `ToggleHUD`. Las demás funciones miembro preparan el componente de aplicación de diagnóstico de gráficos para iniciar o detener la captura activa de información de gráficos, o se deben llamar mientras la aplicación está capturando y registrando información de gráficos en un archivo de registro de gráficos de forma activa.



