---
title: "Elegir una estrategia de implementaci&#243;n del motor de depuraci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "motores de depuración, estrategias de implementación"
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# Elegir una estrategia de implementaci&#243;n del motor de depuraci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilice la arquitectura en tiempo de ejecución para determinar la estrategia de implementación del motor \(DE\) de depuración.  El motor de depuración esté en proceso creado al programa que se va a depurar, en proceso el administrador de depuración de la sesión de \(SDM\) Visual Studio, o el fuera a ambos.  Las instrucciones siguientes pueden ayudarle a elegir entre estas tres estrategias.  
  
## Instrucciones  
 Aunque es posible que el OF está fuera del SDM y el programa que se van a depurar, no hay normalmente razón para hacerlo.  Las llamadas a través de límites de procesos son relativamente lentas.  
  
 Los motores de depuración se ha proporcionado para el entorno de tiempo de ejecución nativo Win32 y para el entorno de Common Language Runtime.  Si debe reemplazar el OF para cualquiera de estos entornos, debe crear el OF en proceso con el SDM.  
  
 Si no, puede elegir entre crear el OF en proceso al SDM o en proceso al programa que se va a depurar.  Es importante tener en cuenta si el evaluador de expresiones de necesita acceso frecuente al almacén de símbolos del programa, y si el almacén de símbolos se puede cargar en memoria para el acceso rápido.  También tenga en cuenta lo siguiente:  
  
-   Si no hay muchas llamadas entre el evaluador de expresiones y el almacén de símbolos, o si el almacén del token se puede leer en el espacio de memoria de SDM, cree el OF en proceso al SDM.  Debe devolver el CLSID del motor de depuración al SDM cuando asocia el programa.  El SDM utiliza este CLSID para crear una instancia de proceso de.  
  
-   Si el OF debe llamar al programa para tener acceso al almacén de símbolos, cree el OF en proceso con el programa.  En este caso, el programa crea la instancia de.  
  
## Vea también  
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)