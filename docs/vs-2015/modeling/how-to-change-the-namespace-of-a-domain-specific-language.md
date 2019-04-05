---
title: Filtrar Cambiar el Namespace de un lenguaje específico de dominio | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2a48c0692dcdcc93d58b5909b03b151ed7e1aae2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987833"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Filtrar Cambiar el espacio de nombres de un lenguaje específico de dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede cambiar el espacio de nombres de un lenguaje específico de dominio. Debe realizar el cambio en el **DSL Explorer**, en las propiedades del proyecto de paquete de Dsl y en la información de ensamblado.  
  
### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Para cambiar el espacio de nombres de un lenguaje específico de dominio  
  
1.  En **DSL Explorer**, haga clic en el **Dsl** nodo.  
  
2.  En el **propiedades** ventana, cambie el **Namespace** propiedad.  
  
3.  Guarde la solución y transformar las plantillas.  
  
4.  En el **proyecto** menú, haga clic en **Dsl propiedades**.  
  
     Aparecerán las propiedades del proyecto.  
  
5.  Haga clic en la pestaña **Aplicación** .  
  
6.  Cambiar el **espacio de nombres predeterminado** propiedad para el nuevo nombre de espacio de nombres.  
  
7.  Si también desea cambiar el nombre del ensamblado, cambie el **propiedad nombre de ensamblado.**  
  
8.  Si ha cambiado el nombre del ensamblado, abra DslPackage\Package.tt y actualice esta línea:  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. Si ha escrito ningún código personalizado, asegúrese de cambiar las referencias de espacio de nombres y clase en los archivos de código.  
  
10. Restablecer la instancia Experimental de Visual Studio.  
  
    1.  Eliminar **\Users\\**_{su nombre}_**\AppData\Local\Microsoft\VisualStudio\\\*Exp**  
  
    2.  En el Windows **iniciar** menú, elija **todos los programas**, **Microsoft Visual Studio 2010 SDK**, **herramientas**, **restablecer el Instancia experimental**.  
  
11. En el **compilar** menú, elija **recompilar solución**.  
  
## <a name="see-also"></a>Vea también  
 [Glosario de las Herramientas del lenguaje específico de dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
