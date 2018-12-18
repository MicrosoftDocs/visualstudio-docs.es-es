---
title: Utilidad CreateExpInstance | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73a6761e844cee41c1a6f0df79f0d6529f4a8215
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768254"
---
# <a name="createexpinstance-utility"></a>Utilidad CreateExpInstance
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use la utilidad CreateExpInstance para crear, restablecer, o elimine una instancia experimental de Visual Studio. Puede usar la instancia experimental para depurar y probar las extensiones de Visual Studio sin cambiar el producto subyacente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Parámetros  
 / Create  
 Crea la instancia experimental.  
  
 O restablecer  
 Elimina la instancia experimental y, a continuación, crea una nueva.  
  
 /Clean  
 Elimina la instancia experimental.  
  
 / VSInstance  
 El nombre del directorio que contiene la instancia de Visual Studio base para copiar.  
  
 / RootSuffix  
 El sufijo para anexar al nombre del directorio de la instancia experimental.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se trabaja en una extensión de Visual Studio, puede presionar F5 para abrir la instancia experimental de forma predeterminada e instalar la extensión actual. Si no está disponible ninguna instancia experimental, Visual Studio crea uno que tiene la configuración predeterminada.  
  
 El número de versión de Visual Studio depende de la ubicación predeterminada de la instancia experimental. Por ejemplo, para Visual Studio 2015, la ubicación es %localappdata%\Microsoft\VisualStudio\14.0Exp\ todos los archivos de la ubicación del directorio se consideran parte de esa instancia. No se cargará a cualquier instancia experimental adicional por Visual Studio a menos que se cambia el nombre del directorio a la ubicación predeterminada.  
  
 Visual Studio no tiene acceso al registro del sistema cuando se abre la instancia experimental. Esto difiere de las versiones anteriores de Visual Studio, que usa una versión experimental del subárbol del registro.  
  
 La utilidad CreateExpInstance reemplaza a la utilidad VsRegEx.  
  
 El ejemplo siguiente restablece la instancia experimental de forma predeterminada de Visual Studio.  
  
 **CreateExpInstance.exe /Reset /VSInstance = 14.0 /RootSuffix = Exp**  
  
## <a name="see-also"></a>Vea también  
 [Publicación de un producto](../../misc/releasing-a-visual-studio-integration-product.md)

