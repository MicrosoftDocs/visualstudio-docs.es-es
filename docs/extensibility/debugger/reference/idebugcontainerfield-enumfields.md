---
title: "IDebugContainerField::EnumFields | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugContainerField::EnumFields"
helpviewer_keywords: 
  - "IDebugContainerField::EnumFields (método)"
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugContainerField::EnumFields
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un enumerador para los campos del contenedor.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumFields(   
   FIELD_KIND         dwKindFilter,  
   FIELD_MODIFIERS    dwModifiersFilter,  
   LPCOLESTR          pszNameFilter,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumFields(  
   enum_ FIELD_KIND      dwKindFilter,   
   enum_ FIELD_MODIFIERS dwModifiersFilter,   
   string                pszNameFilter,   
   NAME_MATCH            nameMatch,   
   out IEnumDebugFields  ppEnum  
);  
```  
  
#### Parámetros  
 `dwKindFilter`  
 \[in\]  Una combinación de constantes de [FIELD\_KIND](../../../extensibility/debugger/reference/field-kind.md) que seleccionar los campos que se van a mostrar.  Las clases de campos pueden describir tipos de almacenamiento, como clase o primitivo, o la información específica, como valor local, parámetro, o puntero “this”.  
  
 `dwModifiersFilter`  
 \[in\]  Una combinación de constantes de [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) que seleccionar los campos que se van a mostrar.  Los modificadores de campos pueden tener permisos de acceso, como public o private, o información de almacenamiento, como virtual, estático, o final.  
  
 `pszNameFilter`  
 \[in\]  El nombre del campo que se va a enumerar.  Esto puede ser un valor NULL si fuese todos los campos a devolverse.  
  
 `nameMatch`  
 \[in\]  Un valor de enumeración de [NAME\_MATCH](../../../extensibility/debugger/reference/name-match.md) que controla si busca distingue entre mayúsculas y minúsculas o no.  
  
 `ppEnum`  
 \[out\]  devuelve un objeto de [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de campos.  Devuelve un valor NULL si no hay campos.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK o S\_FALSE si no hay campos.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 `dwKindFilter`, `dwModifiersFilter`, y los parámetros de `pszNameFilter` se pueden combinar, por ejemplo, para seleccionar todos los métodos virtuales públicos denominados “MyMethod”.  
  
## Vea también  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD\_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME\_MATCH](../../../extensibility/debugger/reference/name-match.md)