# CS 70 Midterm Cheat Sheet — what to write on each side

Copy this by hand (writing it out is half the studying). Front = discrete math structures, Back = number theory + polynomials + counting.

---

## FRONT SIDE

### Logic
- P⟹Q ≡ ¬P∨Q ≡ ¬Q⟹¬P (contrapositive). Converse Q⟹P NOT equivalent. False only when P=T, Q=F. False hypothesis ⟹ vacuously true.
- "P only if Q" / "P sufficient for Q" / "Q necessary for P" / "Q unless ¬P" — all mean P⟹Q.
- De Morgan: ¬(P∧Q)≡¬P∨¬Q; ¬(P∨Q)≡¬P∧¬Q.
- ¬∀xP ≡ ∃x¬P; ¬∃xP ≡ ∀x¬P. Negation flips every quantifier, negates the inside.
- ∀x∃y ≠ ∃y∀x.
- "≥2 distinct x with P": ∃x∃y(x≠y ∧ P(x) ∧ P(y)).

### Proof techniques
- Direct: assume P ⊢ Q. Contraposition: assume ¬Q ⊢ ¬P. Contradiction (for "P" or "doesn't exist"): assume ¬P ⊢ R∧¬R. Cases: exhaustive, prove each.
- a|b ⟺ ∃q∈Z: b=aq. a|b, a|c ⟹ a|(b±c).
- Pigeonhole: n items, k boxes, n>k ⟹ some box ≥2. (Stronger: some box ≥ ⌈n/k⌉.)
- √2 irrational: a/b lowest terms ⟹ a²=2b² ⟹ a even ⟹ b even ⟹ contra.
- Primes infinite: q = p₁⋯pₖ+1 has a prime divisor not among pᵢ.
- Pitfalls: don't assume the claim; don't ÷ by possible 0; negatives flip inequalities; squaring inequalities invalid.

### Induction
- Base case → IH (assume P(k), or strong: P(base..k)) → Step (show P(k+1), SAY where IH is used).
- Strong needed when recursion reaches below k (factorization, postage). Postage 4x+5y ≥ 12: base cases 12,13,14,15.
- If stuck: STRENGTHEN the hypothesis (odd sums: "= n²" not "perfect square"; Σ1/i² ≤ 2−1/n).
- Σᵢ₌₀ⁿ i = n(n+1)/2. Σi² = n(n+1)(2n+1)/6. Σᵢ₌₁ⁿ(2i−1) = n². Σi³ = (n(n+1)/2)².
- Fib: F₀=0, F₁=1, Fₙ=Fₙ₋₁+Fₙ₋₂.
- Well-ordering (N only, not Z, not R): nonempty S⊆N has least element ⟺ induction. "Least counterexample" proofs.
- Horses fail: P(1)⟹P(2) breaks (no overlap).

### Stable Matching (jobs propose)
- Loop: jobs propose to top uncrossed; candidates keep best on string, reject rest; rejected jobs cross off. End when no rejection. ≤ n² days.
- Rogue couple (J,C): BOTH prefer each other to current partners. Stable = none.
- Improvement Lemma: once C receives offer from J (day k), forever after C holds ≥ J. Candidates monotonically improve; jobs decline.
- Terminates with perfect matching; output stable; output is PROPOSER-optimal and RECEIVER-pessimal.
- Optimal partner = best over ALL stable matchings; pessimal = worst.
- Roommates (one pool): stable matching may NOT exist.

### Graphs
- Σ deg(v) = 2e ⟹ # odd-degree vertices is even.
- Path: no repeat vertex. Cycle: closed path. Walk: repeats OK. Tour: closed walk.
- Euler TOUR ⟺ connected (up to isolated) + ALL degrees even. Euler WALK ⟺ connected + exactly 0 or 2 odd.
- Kₙ: n(n−1)/2 edges, degrees n−1.
- Tree ⟺ connected+acyclic ⟺ connected+(n−1 edges) ⟺ minimally connected ⟺ maximally acyclic. Any connected graph: e ≥ n−1. Tree n≥2 has ≥2 leaves.
- Planar connected: v + f = e + 2. Sides: Σsᵢ = 2e, each face sᵢ≥3 ⟹ e ≤ 3v−6. Bipartite/triangle-free: sᵢ≥4 ⟹ e ≤ 2v−4.
- K₅ non-planar (10 > 3·5−6=9). K₃,₃ non-planar (9 > 2·6−4=8; passes 3v−6!). Kuratowski: non-planar ⟺ contains K₅ or K₃,₃.
- Planar ⟹ ∃ vertex of degree ≤ 5. 4-color thm (hard); 5-color provable. Bipartite ⟺ 2-colorable ⟺ no odd cycle. Trees bipartite.
- Hypercube n-dim: V = {0,1}ⁿ, edges = differ in 1 bit. 2ⁿ vertices, n-regular, n·2ⁿ⁻¹ edges, diameter n, bipartite (parity of #1s). Cut: |S| ≤ 2ⁿ⁻¹ ⟹ ≥|S| crossing edges.

---

## BACK SIDE

### Modular arithmetic
- x ≡ y (mod m) ⟺ m | (x−y). Reduce anywhere for +, −, ×.
- x^y mod m: repeated squaring, O(log y) mults. x^{2a}=(x^a)², x^{2a+1}=x(x^a)².
- x⁻¹ mod m exists ⟺ gcd(x,m)=1 (unique). No inverse ⟹ can't cancel; ax≡ay ⇏ x≡y.
- Euclid: gcd(x,y)=gcd(y, x mod y), gcd(x,0)=x.
- Extended Euclid: find a,b: ax+by=gcd. egcd(x,y): if y=0 ret (x,1,0); else (d,a,b)=egcd(y, x mod y); ret (d, b, a−⌊x/y⌋b). If 1=am+bx then x⁻¹ ≡ b (mod m).
- Worked pattern: 1 = 15 − 2·7 = 15 − 2(37−2·15) = 5·15 − 2·37 ⟹ 15⁻¹ ≡ 5 (mod 37).
- Solve ax≡c (mod m), gcd(a,m)=1: x ≡ a⁻¹c. If g=gcd(a,m)>1: solutions exist iff g|c; then g solutions mod m.
- gcd(x,y)=1 ∧ x|yz ⟹ x|z ⟹ unique prime factorization (FTA).
- CRT: nᵢ pairwise coprime, N=Πnᵢ: {x≡aᵢ (mod nᵢ)} has UNIQUE soln mod N. x = Σaᵢuᵢ, uᵢ = (N/nᵢ)·((N/nᵢ)⁻¹ mod nᵢ); uᵢ≡1 (mod nᵢ), ≡0 (mod nⱼ).

### FLT + RSA
- FLT: p prime, gcd(a,p)=1 ⟹ a^{p−1} ≡ 1 (mod p). Reduce exponents mod p−1. Proof: {a·1,…,a·(p−1)} = {1,…,p−1} mod p.
- RSA: N=pq (large primes); e: gcd(e,(p−1)(q−1))=1; d ≡ e⁻¹ mod (p−1)(q−1) ← NOT mod N. Public (N,e), private d.
- E(x)=x^e mod N; D(y)=y^d mod N. Correct: ed = 1+k(p−1)(q−1); x^{ed} ≡ x mod p AND mod q (FLT / x≡0 case) ⟹ ≡ x mod N (CRT).
- Security = factoring N hard; primality testing easy; π(n) ≥ n/ln n (random primes easy to find).

### Polynomials over GF(q), q prime
- Prop 1: nonzero deg-d poly ⟹ ≤ d roots. Prop 2: d+1 points (distinct xᵢ) ⟹ UNIQUE poly deg ≤ d.
- Lagrange: Δᵢ(x) = Πⱼ≠ᵢ(x−xⱼ) / Πⱼ≠ᵢ(xᵢ−xⱼ); p(x) = Σ yᵢΔᵢ(x). Division = ×inverse mod q. Alt: solve linear system in coefficients (good cross-check!).
- Root a ⟹ p(x)=(x−a)q(x). Uniqueness: p−q would have d+1 roots, deg ≤ d ⟹ ≡0.
- Need PRIME mod (field): mod 8, x³ has roots 0,2,4,6.
- Count: deg ≤ d over GF(m), given (d−k) point-values ⟹ m^{k+1} polys. (d+1 given ⟹ 1.)
- Secret sharing, threshold k of n: random deg-(k−1) P over GF(q), q > n,s; P(0)=s; share i = P(i). k shares ⟹ interpolate. k−1 shares ⟹ every secret b consistent with exactly 1 poly ⟹ 0 information.

### Error-correcting codes (Reed–Solomon)
- Message m₁..mₙ → unique deg-(n−1) P, P(i)=mᵢ. Send cⱼ=P(j).
- k ERASURES (known locations): send n+k. Any n points ⟹ interpolate P. Optimal.
- k GENERAL errors (unknown locations): send n+2k (need q > n+2k). Unique: only one deg-(n−1) poly agrees with ≥ n+k of the received values (two would share n points).
- Berlekamp–Welch: E(x)=(x−e₁)⋯(x−eₖ) monic deg k (k unknowns b₀..bₖ₋₁). Q(x)=P(x)E(x), deg n+k−1 (n+k unknowns a₀..aₙ₊ₖ₋₁).
- Q(i) = rᵢE(i) for ALL i=1..n+2k (error pos: E(i)=0; clean pos: P(i)=rᵢ). ⟹ n+2k linear eqs, n+2k unknowns. Solve; P = Q/E; roots of E = error positions. Any solution gives correct P (Q′E=QE′ agree at n+2k pts, deg n+2k−1).

### Counting (order? repetition?)
| | order matters | order doesn't |
|---|---|---|
| w/ replacement | n^k | C(n+k−1, k) stars&bars |
| w/o replacement | n!/(n−k)! | C(n,k) |
- First Rule: sequential choices multiply. Second Rule: count ordered ÷ orderings per outcome.
- C(n,k) = n!/(k!(n−k)!) = C(n,n−k). Permutations of n: n!.
- Anagrams: n!/(m₁!⋯mⱼ!) (mᵢ = letter multiplicities). BERKELEY: 8!/3!.
- Stars & bars: k identical items, n bins = arrange k stars + n−1 bars = C(n+k−1, n−1). Nonneg solns of x₁+⋯+xₙ = k: same. If each xᵢ ≥ 1: substitute yᵢ=xᵢ−1 ⟹ C(k−1, n−1).
- Exactly-type hands: multiply choices per group, e.g., exactly 2 aces in 5 cards: C(4,2)·C(48,3).

### Worked micro-examples (copy these!)
- 3⁴⁵ mod 7: FLT ⟹ 3⁶≡1; 45≡3 (mod 6) ⟹ 3³=27≡6.
- x≡2(5), x≡3(7): u₁=7·(7⁻¹ mod 5)=7·3=21, u₂=5·(5⁻¹ mod 7)=5·3=15; x=2·21+3·15=87≡17 (mod 35).
- RSA toy: p=3,q=11,N=33,(p−1)(q−1)=20,e=7,d=3. 2⁷=128≡29; 29³≡2. ✓
