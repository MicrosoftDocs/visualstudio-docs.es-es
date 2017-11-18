---
title: "Cómo: especificar una ubicación alternativa para las actualizaciones de implementación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: "15"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: a429fa17285018190530ca8058dfb4db7bcb47a2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Cómo: Especificar una ubicación alternativa para las actualizaciones de la implementación
Puede instalar su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación inicialmente desde un CD o un recurso compartido de archivos, pero la aplicación debe buscar actualizaciones periódicas en la Web. Puede especificar una ubicación alternativa para las actualizaciones en el manifiesto de implementación para que la aplicación pueda actualizarse desde el Web después de su instalación inicial.  
  
> [!NOTE]
>  La aplicación debe configurarse para instalar localmente para usar esta característica. Para obtener más información, consulte [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Además, si instala un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación desde la red, establecer una ubicación alternativa, se produce [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usar esa ubicación para la instalación inicial y todas las actualizaciones posteriores. Si instala la aplicación localmente (por ejemplo, desde un CD), la instalación inicial se realiza mediante el medio original y todas las actualizaciones subsiguientes utilizarán la ubicación alternativa.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Especificar una ubicación alternativa para las actualizaciones mediante MageUI.exe (Utilidad basada en formularios Windows Forms)  
  
1.  Abra un símbolo del sistema de .NET Framework y escriba:  
  
     **MageUI.exe**  
  
2.  En el **archivo** menú, elija **abrir** para abrir el manifiesto de implementación de la aplicación.  
  
3.  Seleccione el **opciones de implementación** ficha.  
  
4.  En el cuadro de texto denominado **iniciar ubicación**, escriba la dirección URL del directorio que contiene el manifiesto de implementación para actualizaciones de la aplicación.  
  
5.  Guarde el manifiesto de implementación.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Especificar una ubicación alternativa para las actualizaciones mediante Mage.exe  
  
1.  Abra un símbolo del sistema de .NET Framework.  
  
2.  Establezca la ubicación de actualización mediante el siguiente comando. En este ejemplo, **HelloWorld.exe.application** es la ruta de acceso a la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación, que siempre tiene la extensión de Application, y **http://adatum.com/Update/Path** es la dirección URL que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] comprobará las actualizaciones de la aplicación.  
  
     **Mage-actualizar HelloWorld.exe.application - ProviderUrl http://adatum.com/Update/Path**  
  
3.  Guarde el archivo.  
  
    > [!NOTE]
    >  Ahora debe volver a firmar el archivo con Mage.exe. Para obtener más información, consulte [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 Si instala la aplicación desde un soporte sin conexión como un CD y el equipo está en línea, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] comprueba en primer lugar la dirección URL especificada por el `<deploymentProvider>` etiqueta en el manifiesto de implementación para determinar si la ubicación de actualización contiene una versión más reciente de la aplicación. Si es así, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instala la aplicación directamente desde ahí, en lugar de desde el directorio de instalación inicial, y common language runtime (CLR) determina la confianza de la aplicación con el nivel `<deploymentProvider>`. Si el equipo está sin conexión, o `<deploymentProvider>` no está disponible [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instala desde el CD y el CLR concede confianza basándose en el punto de instalación; para realizar una instalación de CD, esto significa que la aplicación reciba plena confianza. Todas las actualizaciones subsiguientes heredarán ese nivel de confianza.  
  
 Todos los [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las aplicaciones que utilizan `<deploymentProvider>` deben declarar explícitamente los permisos que necesitan en el manifiesto de aplicación, por lo que la aplicación no recibe diferentes niveles de confianza en equipos diferentes.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)