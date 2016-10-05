<p><b>DelayedConstraint</b> delays the application of another constraint until a certain
   amount of time has passed. In it's simplest form, it replaces use of a Sleep 
   in the code but it also supports polling, which may allow use of a longer 
   maximum time while still keeping the tests as fast as possible. 
   
<p>The <b>After</b> modifier is permitted on any constraint, and the delay applies to 
   the entire expression up to the point where <b>After</b> appears. 

<p>Use of a <b>DelayedConstraint</b> with a value argument makes no sense, since 
   the value will be extracted at the point of call. It's intended use is with 
   delegates and references. If a delegate is used with polling, it may be called 
   multiple times so only methods without side effects should be used in this way. 

<table class="constraints">
<tr><th>Syntax Helper</th><th>Constructor</th><th>Operation</th></tr>
<tr><td>After(int)</td><td>DelayedConstraint(Constraint, int)</td></td><td>tests that a constraint is satisfied after a delay.</tr>
<tr><td>After(int, int)</td><td>DelayedConstraint(Constraint, int, int)</td></td><td>tests that a constraint is satisfied after a delay using polling.</tr>
</table>

