---
title: 'Cómo: incluir un archivo de datos en una aplicación ClickOnce | Microsoft Docs'
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
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ee465b3b4524b4f5c530369722f8bdaf36b85227
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582537"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Cómo: Incluir un archivo de datos en una aplicación ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: incluir un archivo de datos en una aplicación ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application).  
  
Cada [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación que se instala se asigna a un directorio de datos en el disco local del equipo de destino donde la aplicación puede administrar sus propios datos. Los archivos de datos pueden incluir cualquier tipo de archivo: archivos de texto, archivos XML o incluso archivos de base de datos (.mdb) de Microsoft Access. Los procedimientos siguientes muestran cómo agregar un archivo de datos de cualquier tipo en su [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación.  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>Para incluir un archivo de datos mediante Mage.exe  
  
1.  Agregue el archivo de datos en el directorio de aplicación con el resto de los archivos de la aplicación.  
  
     Normalmente, será el directorio de la aplicación a un directorio etiquetado con la versión actual de la implementación, por ejemplo, v1.0.0.0.  
  
2.  Actualice el manifiesto de aplicación a la lista el archivo de datos.  
  
     **Mage -u v1.0.0.0\Application.manifest - FromDirectory v1.0.0.0**  
  
     Llevar a cabo esta tarea vuelve a crea la lista de archivos en el manifiesto de aplicación y también genera automáticamente las firmas hash.  
  
3.  Abra el manifiesto de aplicación en el editor XML o texto que prefiera y busque el `file` (elemento) para el archivo agregado recientemente.  
  
     Si agrega un archivo XML denominado `Data.xml`, el archivo tendrá un aspecto similar al siguiente ejemplo de código.  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Agregue el atributo `type` a este elemento y proporcionarla con un valor de `data`.  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Volver a firmar el manifiesto de aplicación con el par de claves o un certificado y, a continuación, volver a firmar el manifiesto de implementación.  
  
     Deberá volver a firmar el manifiesto de implementación porque ha cambiado su hash del manifiesto de aplicación.  
  
     **manifiesto de aplicación de -s de Mage cf - cert_file pwd - contraseña**  
  
     **manifiesto de la aplicación de appm - manifiesto de implementación Mage -u**  
  
     **manifiesto de implementación de -s de Mage cf - certfile pwd - contraseña**  
  
2.  
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Para incluir un archivo de datos mediante MageUI.exe  
  
1.  Agregue el archivo de datos en el directorio de aplicación con el resto de los archivos de la aplicación.  
  
2.  Normalmente, será el directorio de la aplicación a un directorio etiquetado con la versión actual de la implementación, por ejemplo, v1.0.0.0.  
  
3.  En el **archivo** menú, haga clic en **abrir** para abrir el manifiesto de aplicación.  
  
4.  Seleccione el **archivos** ficha.  
  
5.  En el cuadro de texto en la parte superior de la ficha, escriba el directorio que contiene los archivos de la aplicación y, a continuación, haga clic en **rellenar**.  
  
     El archivo de datos aparecerá en la cuadrícula.  
  
6.  Establecer el **tipo de archivo** valor del archivo de datos a **datos**.  
  
7.  Guarde el manifiesto de aplicación y, a continuación, volver a firmar el archivo.  
  
     MageUI.exe le pedirá que vuelva a firmar el archivo.  
  
8.  Volver a firmar el manifiesto de implementación  
  
     Deberá volver a firmar el manifiesto de implementación porque ha cambiado su hash del manifiesto de aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Obtener acceso local o remoto a los datos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)



