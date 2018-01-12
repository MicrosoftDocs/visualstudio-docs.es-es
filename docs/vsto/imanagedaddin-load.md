---
title: 'IManagedAddIn:: Load | Documentos de Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: d6c657698f0d0e3a10871a7276a4eac2617d7874
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Se llama a este elemento cuando se carga un complemento VSTO administrado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*bstrManifestURL*|Ruta de acceso del manifiesto del complemento VSTO.|  
|*pdispApplication*|Un puntero a una interfaz IDispatch que representa la aplicación host que se está cargando el complemento de VSTO.|  
  
## <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT que indica si el método se ha completado correctamente.  
  
## <a name="remarks"></a>Comentarios  
 Un manifiesto es un archivo (normalmente un archivo XML) que proporciona información que se usa para cargar el complemento VSTO. Por ejemplo, un manifiesto puede especificar la ubicación del ensamblado del complemento VSTO y la clase de punto de entrada, para así poder crear una instancia cuando se carga el complemento VSTO.  
  
 El *bstrManifestURL* parámetro contiene el valor de la `Manifest` entrada bajo el HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<nombre de aplicación >*\Addins\\*\<identificador del complemento >* clave del registro para el complemento de VSTO. Para obtener más información, consulta [IManagedAddin Interface](../vsto/imanagedaddin-interface.md).  
  
 Implemente el método [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) para realizar tareas como configurar el dominio de la aplicación y la directiva de seguridad del complemento VSTO que se va a cargar.  
  
## <a name="see-also"></a>Vea también  
 [IManagedAddin Interface](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  