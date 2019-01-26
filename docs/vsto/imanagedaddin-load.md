---
title: IManagedAddin::Load
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 267e2ec1b2ec2dbb5b72a100185ce6b68d455c39
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865897"
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Se llama a este elemento cuando se carga un complemento VSTO administrado.  
  
## <a name="syntax"></a>Sintaxis  
  
```csharp
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*bstrManifestURL*|Ruta de acceso del manifiesto del complemento VSTO.|  
|*pdispApplication*|Un puntero a una interfaz IDispatch que representa la aplicación host que se está cargando el complemento de VSTO.|  
  
## <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT que indica si el método se ha completado correctamente.  
  
## <a name="remarks"></a>Comentarios  
 Un manifiesto es un archivo (normalmente un archivo XML) que proporciona información que se usa para cargar el complemento VSTO. Por ejemplo, un manifiesto puede especificar la ubicación del ensamblado del complemento VSTO y la clase de punto de entrada, para así poder crear una instancia cuando se carga el complemento VSTO.  
  
 El *bstrManifestURL* parámetro contiene el valor de la `Manifest` entrada bajo el **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<nombre de la aplicación >_ \Addins\\_\<ID de complemento >_**  clave del registro para el complemento de VSTO. Para obtener más información, consulte [interfaz IManagedAddin](../vsto/imanagedaddin-interface.md).  
  
 Implemente el método [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) para realizar tareas como configurar el dominio de la aplicación y la directiva de seguridad del complemento VSTO que se va a cargar.  
  
## <a name="see-also"></a>Vea también  
 [IManagedAddin Interface](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
