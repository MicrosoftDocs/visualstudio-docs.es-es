---
title: 'Cómo: crear asociaciones de archivo para una aplicación ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 0cfdbb9262f9a70f3f680554f562ff6c5c2380b5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578983"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Cómo: Crear asociaciones de archivo para una aplicación ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: crear archivo asociaciones para una aplicación ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-create-file-associations-for-a-clickonce-application).  
  
[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] las aplicaciones pueden asociarse con una o varias extensiones de nombre de archivo, por lo que la aplicación se iniciará automáticamente cuando el usuario abre un archivo de esos tipos. Agregar compatibilidad con extensión de nombre de archivo a un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación es sencilla.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>Para crear asociaciones de archivo para una aplicación ClickOnce  
  
1.  Crear un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación normalmente, o usar el existente [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación.  
  
2.  Abra el manifiesto de aplicación con un texto o editor XML, como el Bloc de notas.  
  
3.  Busque el elemento `assembly`. Para más información, consulte [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md).  
  
4.  Como elemento secundario de la `assembly` elemento, agregue un `fileAssociation` elemento. El `fileAssociation` elemento tiene cuatro atributos:  
  
    -   `extension`: La extensión de nombre de archivo que desea asociar a la aplicación.  
  
    -   `description`: Una descripción del tipo de archivo, que aparecerá en el shell de Windows.  
  
    -   `progid`: Una cadena que identifica el tipo de archivo, para marcarlo en el registro.  
  
    -   `defaultIcon`: Un icono que se utilizará para este tipo de archivo. El icono debe agregarse como un recurso de archivo en el manifiesto de aplicación. Para obtener más información, consulta [Cómo: Incluir un archivo de datos en una aplicación ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Para obtener un ejemplo de la `file` y `fileAssociation` elementos, vea [ \<fileAssociation > elemento](../deployment/fileassociation-element-clickonce-application.md).  
  
5.  Si desea asociar más de un tipo de archivo a la aplicación, agregue más `fileAssociation` elementos. Tenga en cuenta que el `progid` atributo debe ser diferente para cada uno.  
  
6.  Cuando haya terminado con el manifiesto de aplicación, vuelva a firmar el manifiesto. Puede hacerlo desde la línea de comandos mediante el uso de Mage.exe.  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     Para obtener más información, consulte [Mage.exe (Manifest Generation and Editing Tool)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)  
  
## <a name="see-also"></a>Vea también  
 [\<fileAssociation > elemento](../deployment/fileassociation-element-clickonce-application.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (Herramienta de generación y edición de manifiestos)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)



