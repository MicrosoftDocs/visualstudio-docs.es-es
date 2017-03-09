---
title: "C&#243;mo: Cambiar la m&#225;quina de reproducci&#243;n de diagn&#243;sticos de gr&#225;ficos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Cambiar la m&#225;quina de reproducci&#243;n de diagn&#243;sticos de gr&#225;ficos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede reproducir información de gráficos mediante el equipo local, o mediante un equipo remoto o el dispositivo.  
  
## Elección de un equipo de reproducción  
 El equipo de reproducción es un equipo o un dispositivo que se usa para reproducir eventos de gráficos desde un registro de gráficos.  Normalmente el equipo local es la opción más adecuada pero puede que un problema de representación no se reproduzca en un equipo con hardware o versiones de controlador diferentes al del equipo donde se capturó; cuando esto suceda, puede elegir una máquina de reproducción remota que reproduce mejor el problema y seguir usando el equipo de desarrollo para diagnosticarlo.  
  
#### Para utilizar el equipo local para reproducir información de gráficos  
  
1.  En la ventana de documento de registros de gráficos, elija el vínculo **Máquina de reproducción**.  Aparece el cuadro **Conexiones del depurador remoto**.  
  
2.  En **Configuración manual**, en la propiedad **Dirección**, escriba `localhost`.  
  
3.  Establezca la propiedad **Modo de autenticación** en **Ninguna**.  
  
4.  Elija el botón **Seleccionar**.  
  
#### Para utilizar un equipo remoto a fin de reproducir la información de gráficos  
  
1.  En la ventana de documento de registros de gráficos, elija el vínculo **Máquina de reproducción**.  Aparece el cuadro **Conexiones del depurador remoto**.  
  
2.  En **Configuración manual**, en la propiedad **Dirección**, escriba el nombre de dominio de Windows o la dirección IP del equipo o dispositivo que desea utilizar para reproducir la información de gráficos.  
  
3.  Especifique la clase de autorización que desea utilizar para proteger la conexión al equipo de reproducción.  
  
    -   Para la Autenticación de Windows, establezca la propiedad de **Modo de autenticación** en **Windows**.  
  
    -   Para ninguna autenticación, establezca la propiedad **Modo de autenticación** en **Ninguna**.  
  
4.  Elija el botón **Seleccionar**.  
  
> [!NOTE]
>  El cuadro de diálogo **Conexiones del depurador remoto** también podría mostrar destinos de depuración remota que están conectados directamente con su equipo de desarrollo o están en la misma subred.  Puede utilizar uno de estos destinos de depuración remota como el equipo de reproducción de diagnósticos de gráficos sin configurarlo manualmente.  En el cuadro **Conexiones del depurador remoto**, seleccione el destino deseado y elija el botón **Seleccionar**.  
  
## Vea también  
 [Documento de registro de gráficos](../debugger/graphics-log-document.md)