# 漫反射辐照

原文     | [Diffuse irradiance](https://learnopengl.com/#!PBR/IBL/Diffuse-irradiance)
      ---|---
作者     | JoeyDeVries
翻译     | [Redknot](https://github.com/redknotmiaoyuqiao)
校对     | 暂无

!!! Important

	注意： 作者正在对PBR章节进行大的调整，原文的内容时时可能有更新，建议仍是阅读原文。

!!! Important

IBL <def>基于图像的光照技术</def>(image based lighting) 是一种使用collection来照亮物体的技术，和从前课程中直接分析光照是不一样的，但是我们仍然可以将环绕周围的环境看作是一个大的光源。这通常使用一个 cubemap 的环境贴图（从现实世界中或从一个三维场景生成）我们可以使用我们的照明方程：处理每个立方体贴图像素的发光体。这样，我们就可以有效地捕捉环境的全局光照和一种自然的感觉。给予对象一个更好地融入周围的环境中。

由于基于图像的照明算法是捕获环境的光照，它的输入通常是更加精细的环境光，甚至是较为粗略的全局光照（GI）。当我们使用环境光照时，IBL 可以使我们的 PBR 材质更加接近真实物理材质。

开始介绍IBL进入我们的PBR系统让我们再看一眼的反射方程：

Lo(p,ωo)=∫Ω(kdcπ+ksDFG4(ωo⋅n)(ωi⋅n))Li(p,ωi)n⋅ωidωi
