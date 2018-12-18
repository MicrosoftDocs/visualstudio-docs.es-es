---
title: 'Cómo: deshabilitar la activación de direcciones URL de aplicaciones ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 47fc07ade4529ab99a4c687ea62791ec083d2d0b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273338"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Cómo: Deshabilitar la activación de direcciones URL de aplicaciones ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Normalmente, una aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] se inicia automáticamente después de que se instale desde un servidor web. Por motivos de seguridad, puede decidir deshabilitar este comportamiento e indicar a los usuarios para iniciar la aplicación desde el **iniciar** menú en su lugar. En el procedimiento siguiente, se describe cómo deshabilitar la activación de URL.  
  
 Esta técnica se puede utilizar solo para las aplicaciones [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instaladas en el equipo del usuario desde un servidor web. No se puede utilizar para aplicaciones solo en línea, que se pueden iniciar utilizando su dirección URL. Para obtener más información sobre la diferencia entre las aplicaciones sólo en línea e instaladas, consulte [elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Este procedimiento utiliza la herramienta [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] MageUI.exe. Para obtener más información sobre esta herramienta, consulte [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). También puede realizar este procedimiento mediante [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="procedure"></a>Procedimiento  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Deshabilitar la activación de direcciones URL para la aplicación  
  
1.  Abra el manifiesto de implementación en MageUI.exe. Si aún no ha creado uno, siga los pasos descritos en [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Seleccione el **opciones de implementación** ficha.  
  
3.  Desactive el **ejecutar automáticamente la aplicación después de instalar** casilla de verificación.  
  
4.  Guarde y firme el manifiesto.  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)



