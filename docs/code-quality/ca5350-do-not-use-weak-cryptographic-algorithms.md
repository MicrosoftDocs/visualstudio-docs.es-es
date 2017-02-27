---
title: "CA5350: No use algoritmos criptogr&#225;ficos no seguros | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA5350: No use algoritmos criptogr&#225;ficos no seguros
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseWeakCryptographicAlgorithms|  
|Identificador de comprobación|CA5350|  
|Categoría|Microsoft.Cryptography|  
|Cambio problemático|No trascendental|  
  
> [!NOTE]
>  Esta advertencia se actualizó por última vez en noviembre de 2015.  
  
## Motivo  
 Los algoritmos de cifrado como <xref:System.Security.Cryptography.TripleDES> y los algoritmos hash como <xref:System.Security.Cryptography.SHA1> y <xref:System.Security.Cryptography.RIPEMD160> se consideran no seguros.  
  
 Estos algoritmos criptográficos no proporcionan tantas garantías de seguridad como sus equivalentes más modernos. Los algoritmos hash criptográfico <xref:System.Security.Cryptography.SHA1> y <xref:System.Security.Cryptography.RIPEMD160> proporcionan menos resistencia a colisiones que los algoritmos hash más modernos. El algoritmo de cifrado <xref:System.Security.Cryptography.TripleDES> proporciona menos bits de seguridad que los algoritmos de cifrado más modernos.  
  
## Descripción de la regla  
 Las funciones hash y los algoritmos de cifrado no seguros se usan hoy en día por varios motivos, pero no deben usarse para garantizar la confidencialidad o la integridad de los datos que protegen.  
  
 La regla se desencadena cuando encuentra los algoritmos 3DES, SHA1 o RIPEMD160 en el código y lanza una advertencia al usuario.  
  
## Cómo corregir infracciones  
 Use opciones de criptografía más segura:  
  
-   Para el cifrado TripleDES, use el cifrado <xref:System.Security.Cryptography.Aes>.  
  
-   Para las funciones hash SHA1 o RIPEMD160, use los de la familia [SHA\-2](https://msdn.microsoft.com/en-us/library/windows/desktop/aa382459.aspx) \(por ejemplo, <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384> y <xref:System.Security.Cryptography.SHA256>\).  
  
## Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla cuando el nivel de protección necesario para los datos no requiera una garantía de seguridad.  
  
## Ejemplo de pseudocódigo  
 En el momento de redactar este artículo, el ejemplo de pseudocódigo siguiente muestra el patrón que esta regla detecta.  
  
### Infracción de hash SHA\-1  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA1.Create();  
  
```  
  
### Solución  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA256.Create();  
  
```  
  
### Infracción de hash RIPEMD160  
  
```  
using System.Security.Cryptography; ... var hashAlg = RIPEMD160Managed.Create();  
  
```  
  
### Solución  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA256.Create();  
  
```  
  
### Infracción de cifrado TripleDES  
  
```  
using System.Security.Cryptography; ... using (TripleDES encAlg = TripleDES.Create()) { ... }  
```  
  
### Solución  
  
```  
using System.Security.Cryptography; ... using (AesManaged encAlg = new AesManaged()) { ... }  
```