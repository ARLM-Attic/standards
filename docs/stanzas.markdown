---
Title: Code Stanzas
---

One of the basic forms of code organization is a block of code. Like a paragraph in writing, a block of code should have a relatively precise purpose and the lines within a block should be related to that purpose. Furthermore, a code block should be documented with comments to explain its purpose.

It may seem like a simple (and probably obvious) idea, but it is a common grouping of code and we like those blocks to have common organization.

The most basic format of a stanza code block is (examples will be in C# but apply to all languages):

	// Move the current index into the previous so we can refer to it later.
	previousIndex = currentIndex;

The comment *must* be included in a stanza. It should describe [why](why) we wrote the code. Comments don't have to include what we're doing simply because the code explains the what; we need the comment to explain why.

# Newlines

The code in the stanza can be broken apart with whitespace if it makes it easier to understand.

	// Set up the initial variables for the loop below.
	int multiplier = input.Multiplier * 2;
	HashSet<string> seenKeys = new HashSet<string>();
	
	foreach (string key in input.Keys)
	{
		if (seenKeys.Add(key))
		{
			modifiedValues[key] *= multiplier;
		}
	}

Typically, we group the variable decalarations in a group at the top, but this isn't required since frequently we extract variables to create new objects.

# Scope

Stanzas apply until the next stanza or the end of an inner scope, regardless of the code or newlines inside them. For example:

	// This comment applies to all the code until the next stanza comment. It
	// will explain
	doSomething();
	doSomething();
	
	foreach (var stuff in box)
	{
		doSomething(stuff);
	}
	
	doSomething();
	
	// This comment applies to the code following it.
	doSomethingElse();

If the code includes inner scopes, such as loops, the stanza applies to the entire loop if not commented. In the above example, the foreach code is explained by the "This comment applies..." comment.

An inner scope can be commented and the comment applies to the next comment or the end of the scope. It will also will apply to the comment in the outer scope.

	// This comment applies to all the code until the next stanza comment. It
	// will explain
	foreach (var stuff in box)
	{
		// The following code is explained by both this comment and the outer
		// "This comment applies..." line. It includes the following two
		// statements.
		doSomething(stuff);

		doSomethingNew(stuff);
		
		// This comment includes the following line. The code is also explained by
		// the "This comment applies..." comment.
		doSomethingSpecial(stuff);
	}
	
	// This comment applies to the code following it.
	doSomethingElse();
	
If an inner scope has a comment, then all code blocks need to be commented. The following *is not* allowed:

	// This comment applies to all the code until the next stanza comment. It
	// will explain
	foreach (var stuff in box)
	{
		doSomething(stuff);

		// This comment includes the following line. The code is also explained by
		// the "This comment applies..." comment.
		doSomethingSpecial(stuff);
	}
	
Putting a comment above the "doSomething(stuff);" line would correct the problem.

It is acceptable to have a comment at the end of a scope that explains the state coming out of the scope.

	// This comment applies to all the code until the next stanza comment. It
	// will explain
	foreach (var stuff in box)
	{
		// The following code is explained by both this comment and the outer
		// "This comment applies..." line. It includes the following two
		// statements.
		doSomething(stuff);
		
		// At this point, the `stuff` variable has been populated with something.
	}
	
# Justfication

This is probably a very basic thing in coding, but most standards don't discuss it. Organizing the code into stanzas has a few purposes. First is that it encourages commenting. When writing code that is read and maintained by multiple people, good commenting is critical to understanding. Likewise, what is "obvious" one day may not be three years down the line.

Second, this organization guides developers to writing focused code. When the comment applies to everything underneath it, the code can be taken as a whole instead of needing to be parsed line-by-line. Likewise, if there are a large number of one comment/one line blocks, maybe the code could use some organization. Then again, it may be perfectly appropriate for a single line to be heavily commented for understandability.