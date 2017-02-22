---
title: "Depurar un control ActiveX enlazado a datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX, depurar"
  - "controles [Visual Studio], ActiveX"
  - "controles enlazados a datos, ActiveX"
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurar un control ActiveX enlazado a datos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si está desarrollando un control ActiveX que se enlazará a un control de origen de datos, puede crear su propia aplicación contenedora y utilizar dicho contenedor para depurar el control ActiveX.  
  
 Por ejemplo, puede crear una aplicación MFC basada en cuadros de diálogo y colocar el control enlazado a datos y un control de origen de datos en el cuadro de diálogo.  Puede utilizar esta aplicación MFC para la comprobación en tiempo de ejecución y como contenedor ejecutable para depurar el control ActiveX enlazado a datos.  
  
## Utilizar Test Container  
 Si desea un contenedor que pueda modificar fácilmente para que admita diversas interfaces tanto en el control como en el contenedor, utilice ActiveX Test Container como archivo ejecutable para la sesión de depuración.  En ActiveX Test Container, haga clic en **Opciones**, en el menú **Contenedor**, para habilitar diversas interfaces.  Para obtener más información, vea [Probar propiedades y eventos con un contenedor de prueba](/visual-cpp/mfc/testing-properties-and-events-with-test-container).  
  
 Si necesita ejecutar paso a paso el código del contenedor mientras realiza la depuración, utilice la versión de depuración del contenedor o emplee la versión del depurador de ActiveX Test Container.  Para obtener más información, vea [TSTCON Sample: ActiveX Control Test Container](http://msdn.microsoft.com/es-es/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## Vea también  
 [Depurar COM y ActiveX](../debugger/com-and-activex-debugging.md)   
 [Controles ActiveX](/visual-cpp/mfc/activex-controls)