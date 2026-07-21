RESPONSE TO KR 2026 REVIEWERS

 

We would like to thank the three reviewers for their helpful comments.

 

RESPONSE TO REVIEW 1

 

Formulas with nested strategic modalities are useful for reasoning about scenarios in which a first coalition has the capacity (i) to make a second coalition a danger,

while the second coalition is not a danger in the initial state, or (ii) to make a second coalition harmless, while the second coalition is a danger in the initial state,

In other words, through the nesting of modalities, our logic supports reasoning about danger-enabling and danger-disabling actions or strategies in multi-agent settings.

Analogously, nesting modalities allows us to represent situations in which a first coalition has the capacity to make a second coalition a potential benefactor by choosing a certain strategy,

while the latter is not a potential benefactor in the initial state.

 

For example, we can use our language to represent the fact that, in the example given in the paper, the coalition consisting of robots 0 and 1 has a strategy that is strongly beneficial

to robot 0 and guarantees that, in the next state, robot 0 becomes a danger to the coalition consisting of robots 1 and 2. However, in the current state, robot 0 is not a danger to that coalition.

This situation is captured by the following formula:
 

<<{0,1}:{0}, ∅>>Danger({0},{1,2}) ∧ ¬Danger({0},{1,2})


Given the abbreviation for Danger introduced in Section 5, this is equivalent to the nested formula:
 

<<{0,1}:{0}, ∅>><<{0}:∅,{1,2}>>X ⊤ ∧ <<{0}:∅,{1,2}>> X ⊤

 

Intuitively, in the initial situation, robot 0 is not a danger to the coalition {1,2}, since the two robots can collaborate to block the passages to the rooms they are guarding.

However, agent 1 may leave the passage to its room unguarded, allowing robot 0 to exploit this opportunity and enter the room. As a result, robot 0 becomes a permanent danger

to both robots 1 and 2, as it can choose to remain in the room indefinitely, thereby preventing them from achieving their goal of keeping robot 0 out of either room.


Our conjecture is that model checking in our language is exponential. This is because verifying a welfare-affecting strategic capability requires considering all strongly beneficial

(respectively, harmful) strategies that one coalition may have with respect to another, and the number of such strategies is exponential. However, we believe that model checking

becomes polynomial when restricted to classes of models in which agents’ preferences depend only on the next states. In this case, instead of considering sets of strongly beneficial

(respectively, harmful) strategies, it suffices to consider strongly beneficial (respectively, harmful) actions. This restriction would allow the use of the polynomial-time model-checking

algorithm introduced by Alur, Henzinger, and Kupferman (2002) for ATL. We leave a detailed investigation of model checking to future work, as our KR submission focuses on satisfiability checking.
 

RESPONSE TO REVIEWER 2
 

We focus on regular preferences because we believe they are more interesting from an axiomatic perspective.

If we drop the assumptions of well-foundedness and converse well-foundedness of preferences,

then Axioms A-WFP and A-CWFP must also be removed from the axiomatization. Similarly, if we drop non-flatness,

Axiom A-BHC must be removed. We believe that doing so would make the logic weaker and less interesting.

We will clarify this point in the revised version of the paper.

 

We agree that axiomatizing the full language is an important issue, and we plan to address it in future work. However, even obtaining

an axiomatization of the until-free fragment, including the henceforth/always modality, via a novel canonical argument was a non-trivial task and required significant effort.

In particular, it involved developing a new technique based on the notion of a canonical model under a formula context, and using it to prove the completeness theorem.

Extending the completeness result to the full language with the until operator is non-trivial in either standard completeness proofs for ATL or our setting. In standard completeness proofs for ATL, the truth lemma for formulas involving until relies crucially on the co-strategy semantics, which requires reasoning about sets of paths in a global way.

In our approach, the canonical construction is context-dependent: maximal consistent sets are taken with respect to a finite closure of the formula, rather than being fully maximal in the classical sense. As a consequence, the truth lemma is formulated in terms of derivability rather than simple membership.

While this is sufficient for the until-free fragment, difficulties arise when handling until. In particular, the co-strategy semantics requires a condition of the following kind: if the negation of a formula is not derivable from the canonical set, then the formula should be satisfied at the corresponding state. This implication is essential for establishing the truth lemma for until-formulas, but it is not guaranteed by our current context-restricted canonical construction.

Addressing this issue would require strengthening the construction so as to ensure this property, or alternatively developing a different technique to handle eventualities in the presence of strategic and preference constraints. We are currently investigating possible approaches, but it is not yet clear whether such an extension can be achieved. For this reason, we leave the axiomatization of the full language with until for future work.

To the best of our knowledge, we are the first to establish completeness of an ATL safety fragment using a canonical model argument.

 

Thanks for pointing out the typos and formatting issues. We will correct them.


 

RESPONSE TO REVIEWER 3
 

Response to Q1, Q2, Q3

 

There is a clear connection between our logical approach and game theory. Concurrent game frames with regular preferences, on which our logical language is interpreted,

generalize extensive games by allowing more than one player to act at a given stage. In contrast, in the standard definition of extensive games, only one player acts at each node.

 

However, the concepts we formalize in the paper and illustrate in Figure 1, namely, the welfare-affecting strategic capability of a coalition relative to another coalition, and the

derived notions discussed in our response to Reviewer 1, namely danger-enabling and danger-disabling strategic capability (i.e., the ability of one coalition

to make another coalition dangerous or harmless by choosing a certain strategy), can only be partially represented using extensive-form games.
 

In particular, in our logical approach we can fully represent the notion of a coalition's welfare-affecting strategic capability relative to another coalition, that is, statements of the form:
 

"a coalition C can choose a strategy (i) that is strongly harmful (resp. beneficial) to another coalition

H (resp. B), and (ii) that guarantees that a certain temporal property (expressed by an LTL formula) φ holds."
 

For example, as shown in Example 3 (Cont.) in Section 5, our language allows us to represent that, in the three-robot scenario of Figure 1, robots 1 and 2 
have a strategy that is strongly harmful to robot 0 and beneficial to themselves, and that prevents robot 0 from reaching either the left room or the right 
room at some point in the future. This cannot be fully represented in a game-theoretic framework. In particular, using extensive games we can only represent part 
(i) of the above statement. In the example, using game-theory, we can only represent the fact robots 1 and 2 have a strategy that is strongly harmful to robot 0 
and beneficial to themselves, but we cannot represent the rest of the sentence, namely, the fact that such strategy prevents robot 0 from reaching 
either the left room or the right room at some point in the future.
 

This is because game theory does not provide a logical language to express the content of a coalition's welfare-affecting strategic capability, which in our approach is captured by a LTL formula.
 

Another limitation of the game-theoretic approach, compared to our logical approach, is that it allows us to represent the concept of welfare-affecting strategic capability and 
its derived notions, such as danger-enabling and danger-disabling capability, but not to reason about them. This is because game theory operates only at the semantic 
level and does not distinguish between the semantic level and the level of a logical language. By contrast, in our approach, we can both represent these concepts, via the 
semantics of concurrent game frames with regular preferences, and reason about them through the logical language introduced in Section 5, which is interpreted over this semantics.

 

The reasoning component of our approach is captured by the sound and complete axiomatization provided in Section 6. Moreover, the complexity results for satisfiability checking presented in Section 7
(in particular, Corollary 1) highlight the complexity of reasoning about the concept of welfare-affecting strategic capability and its derived concepts within our framework.


 

To the best of our knowledge, there is no approach in the literature that clearly separates the semantic level from the language level in such a way that (i) the 
concept of welfare-affecting strategic capability and its derived notions can be fully represented, and (ii) reasoning about these concepts is supported. 
Our logical approach fills this gap.

 

Response to Q4
 

The use of strict temporal operators is mainly for technical reasons, as it simplifies the proof of completeness of the axiomatization.
[CAN WE SAY MORE HERE: why it simplifies the proof]
This is essentially a stylistic choice, since strict and non-strict temporal operators are interdefinable.