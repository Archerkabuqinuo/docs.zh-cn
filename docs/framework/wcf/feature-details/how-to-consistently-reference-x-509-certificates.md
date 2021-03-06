---
title: 如何：以一致的方式引用 X.509 证书
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
ms.openlocfilehash: efc4fb399224de7f03c6bffb606178184de1d467
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489380"
---
# <a name="how-to-consistently-reference-x509-certificates"></a>如何：以一致的方式引用 X.509 证书
可以采用下列多种方式来标识证书：证书哈希、颁发者和序列号或者使用者密钥标识符 (SKI)。 SKI 为证书的使用者公钥提供唯一标识，通常用于处理 XML 数字签名。 SKI 值通常为形式的 X.509 证书的一部分*X.509 证书扩展*。 Windows Communication Foundation (WCF) 具有一个默认*引用样式*如果 SKI 扩展，则证书中缺少使用颁发者和序列号。 如果证书中包含 SKI 扩展，该默认引用样式将使用 SKI 来指向证书。 如果在开发过程中应用程序，使用不使用 SKI 扩展的使用 SKI 扩展的证书的证书，则使用 WCF 生成消息中的引用样式也会更改。  
  
 如果无论是否存在 SKI 扩展，都需要使用一致的引用样式，则可以配置所需的引用样式，如下面的代码中所示。  
  
## <a name="example"></a>示例  
 下面的示例创建一个自定义安全绑定元素，该元素使用一致的引用样式：颁发者名称和序列号。  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>编译代码  
 编译该代码需要以下命名空间：  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a>请参阅  
 [使用证书](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
