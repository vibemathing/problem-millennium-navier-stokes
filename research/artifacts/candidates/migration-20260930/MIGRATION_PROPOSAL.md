# navier-stokes: blocked migration and archived research proposal

Status: proposal_only / not admitted. Date: 2026-09-30 UTC.
Base revision: b47804fac940da277b6f756a925bb009dd409545. Problem: problem:millennium-navier-stokes.
Contract digest: 4abdbffa2325e8421662fa31897c55976eb2d405f47729d4af0b31fc187fbc0f. Harness: 1.2.4.

## Bootstrap and migration boundary

Fresh default branch has verified repository identity, active canonical-admitted ProblemContract, but empty attempts and obligation-graphs. No admitted Attempt/Route/Graph/target Obligation exists. Therefore no new mathematical research was started. This PR archives the relevant previously written exploratory derivations for review and proposes admission work. Proposed node labels and IDs are not admitted records. No canonical record, Harness file, schema, script, workflow, EvidenceLink, Result, verifier receipt, or Solution view is changed.

The profile remains candidate_generator_and_transport_writer, even under an owner GitHub principal. Harness maintenance cannot include candidate artifacts or change canonical truth. Source repair below is a proposed input for a trusted migration, not a changed ProblemContract. Baseline make check-full passed (8 tests, 1 skipped); this does not establish current-template compatibility. Current template requires source revision/content_sha256/quote/license fields missing from canonical records.

The existing PR diff gate requires exactly one valid web-attempt packet. None is fabricated here because pre-admission objects are absent. Expected exact failure: `candidate PR must add exactly one web attempt packet, found 0`. Do not merge this proposal-only draft or weaken the gate to make it pass. A trusted operator must review and admit the Attempt and graph, confirm source provenance/license treatment, and then produce a correctly bound packet.

## Archived local research (not new repository execution)

The following text was developed before this migration and has candidate-only scope. Its references to executed assertions concern the earlier local exploration, not a verifier receipt or this repository's CI. Original combined draft SHA-256: d05ccad5b75594a1380c2e3c9d4f7405c90885c0c83a2be6a85935309d266e84. Original script SHA-256: 4fadc66faf3e39dfdb616d8316412f67ef516b297ff0b93f32783f1d64bbf4da. No full third-party paper is republished.

## 1. NS 根：必须先纠正时间状态

### 1.1 官方数学范围

使用三维不可压方程

∂ₜu+(u·∇)u=νΔu−∇p+f， div u=0，u(0)=u₀，ν>0。

[Fefferman 官方陈述](https://www.claymath.org/wp-content/uploads/2022/06/navierstokes.pdf) 给出四种接受分支：A/B 对全空间/三维周期域、任意规定光滑散度零初值、零外力，证明全局光滑解；C/D 在相应域给出允许的光滑初值和外力，使指定全局解不存在。全空间初值及外力要求任意阶导数的任意多项式衰减，解满足规定有限能量条件；周期分支要求周期性，外力时间衰减。必须选定分支后逐条回读官方条件，不能用二维、可压、Euler、平均方程或特殊解替换。

A 的否定是存在一个允许初值在 f=0 时没有指定全局光滑解。C 允许 f≠0，因而 C 成立不逻辑蕴含 ¬A；D 与 B 同理。整个“完成任一接受分支”的元目标不是把四个结论合取。

### 1.2 2026 新声明审计

[Clay 2026-09-11 公告](https://www.claymath.org/news/navier-stokes-announcement/) 使用 “apparently been settled”，并明确评价流程仍将进行。故当前不应无条件称“六题全部仍未解”，也不能说本包验证了新解。

[OpenAI 原始论文](https://cdn.openai.com/pdf/32d9f210-8b73-45e0-91bc-82a30aef8a9a/navier-stokes.pdf)，署名 OPENAI，题为 *Finite Time Blowup for Navier–Stokes*：Theorem 1.1 声称对每个 ν>0 存在 f∈C∞c(R³×(0,∞))、固定紧集 K，零初值解在 t<1 光滑，速度和压强支撑于 K，L² 一致有界而 L∞ 在 t↑1 无界；Corollary 10.6 给出周期对应结果，作者分别映射到 C、D。论文中的外力是跨越 t=1 的全局光滑紧支撑函数，不仅是 t<1 光滑。读到声明不等于验证这些存在性断言。

紧支撑为何符合 Clay 外力衰减：若任意 D=∂x^α∂t^j f 连续并支撑在固定紧集 S，则对每个整数 K≥0，C=max_S(1+|x|+t)^K|D f| 有限，S 外导数为零；即所需界。周期域同理只保留时间权重。难点是证明残差真的全阶光滑延拓，不能仅由 u,p 在 t<1 光滑推出。

### 1.3 NS 六个子问题及 DAG

有向边 X→Y 的统一含义：Y 的此条证明/审计路线使用 X，不宣称 X 单独充分，更不宣称等价。多个入边默认 AND；不同 root 分支明确 OR。

- N1 `definition`：冻结 A/B/C/D 与新声明逐项匹配；来源审计已完成到定理陈述层，证明可靠性未核验
- N2 `lemma`：ν=1 到任意 ν>0 及固定 ν 下空间时间缩放；本包推导与符号检查完成
- N3 `lemma`：新构造在奇时的残差全阶延拓及紧支撑；作者声称已证，本包未验证。普通截断会引入导数项，必须控制
- N4 `theorem`：构造解的能量界、速度发散、以及唯一性比较排除另一全局光滑解；作者声称已证，本包未验证。不能只展出一个坏弱解
- N5 `theorem`：在固定小立方体内部支撑、时间平移拼接、周期延拓推得 D；作者声称已证，本包只核验变换代数，没有核验构造前提
- N6 `counterexample_target`：驳斥“L² 控制可直接控制任意三维散度零场 H¹”的捷径；本包给出精确反例族。它不是 NS 解的爆破反例

路线图：N1+N2+N3+N4→C（待审）；C 的具体紧支撑构造+N2+N5→D（待审）；C OR D→官方根关闭候选（另需独立验证与状态评审）。N6→“排除纯瞬时 L²→H¹ 捷径”，这是路线约束边，没有 N6→C/D/¬A/¬B 的蕴含。

本次不把 A/B 自动升级为已解决或已否定，也不把“本文未核验”说成“文献未证明”。如后续研究 A/B，须单独冻结零外力量词并完成最新状态检索；本包只证明 C/D 的声明本身没有逻辑消除 A/B。

## 2. NS 已执行数学：变换与能量障碍

### 2.1 任意黏度变换（条件引理）

假定 (u,p,f) 在 Ω×I 上光滑并满足黏度1方程。对任意 ν>0 定义 y=x/√ν，

uν(x,t)=√ν u(y,t)，pν(x,t)=νp(y,t)，fν(x,t)=√ν f(y,t)。

链式法则逐项给出：∂ₜuν=√ν∂ₜu；(uν·∇x)uν=√ν(u·∇y)u；νΔxuν=√νΔyu；∇xpν=√ν∇yp；divx uν=divy u。因此整个残差是原残差的 √ν 倍，定义域为 √ν Ω×I。变量替换 dx=ν^(3/2)dy 给出 ||uν(t)||₂²=ν^(5/2)||u(t)||₂²；||uν(t)||∞=√ν||u(t)||∞；支撑放大 √ν，奇时不变。ν=0 不在此引理范围。

固定黏度的另一变换：ũ(x,t)=λu(λx,λ²(t−t₀))、p̃=λ²p、f̃=λ³f，λ>0。方程每项获得 λ³；L² 平方获得 λ⁻¹；支撑缩小 λ⁻¹。要取 t₀=1−λ⁻² 并在此前拼接零，必须原解在原时间0附近确实为零到所需阶。光滑零初值单独不足以允许任意强行拼接；若 f 支撑远离0，则用相应光滑解唯一性才能得到这一性质。这是 N5 的明确未核查前提。

否定形式：存在满足前提的光滑三元组和某 ν>0，使上述任一方程/散度/范数关系失效。本推导排除该否定；没有证明满足前提的爆破解存在。

### 2.2 瞬时能量控制的精确失败族

取 φ(x,y,z)=exp(−x²−y²−z²)，v=(−2yφ,2xφ,0)。这是 Schwartz 场，div v=4xyφ−4xyφ=0。直接高斯积分得

E=∫|v|²=π^(3/2)/√2，G=∫|∇v|²=5π^(3/2)/√2。

对任意 λ>0 取 wλ(x)=λ^(3/2)v(λx)。则 div wλ=0，||wλ||₂²=E，||∇wλ||₂²=λ²G。令 λ→∞，证明不存在只依赖 E、对所有这类场都有限的梯度上界 F(E)。即使令 v/E^(1/2) 标准化为单位 L² 也一样。每个场都满足允许的初值型空间正则/衰减，但它们不是同一条 NS 轨道，更不说明正时间爆破。这个反例仅针对瞬时范数估计；没有否定利用时间耗散、初值更高范数或非线性结构的 PDE 方法。

[陶哲轩平均 NS 原始论文](https://arxiv.org/abs/1402.0290) 进一步说明保持能量消去性质的修改方程仍能爆破，提示必须使用真实非线性更细结构；它也不是原方程的反例。

执行结果：divergence=0；E=√2π^(3/2)/2；G=5√2π^(3/2)/2；G/E=5；λ=1,2,4,8 的梯度平方按1,4,16,64增长。符号断言全部通过。失败准则：任一残差不为零、积分不收敛、结果常数不匹配即失败；不设经验“似乎足够准确”的容差。

