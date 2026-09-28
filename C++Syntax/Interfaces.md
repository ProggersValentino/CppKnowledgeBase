[cpplearn](https://www.learncpp.com/cpp-tutorial/pure-virtual-functions-abstract-base-classes-and-interface-classes/)

unlike GOlang or C#, C++ does not have a dedicated keyword for `interface`. 

Interfaces in C++ are normal classes prefixed with `I` in their definition name where it contains only **pure** virtual functions to be implemented by other class:
```cpp
class IDamagable
{
public:
	//virtual functions that are assigned a value of 0 are pure
	virtual int ApplyDamage(int dmg) = 0;
	
	virtual ~IDamagable() //deconstructor 
}
```

As you can see we assign the virtual function to a value of `0` as indicator to C++ that it is a pure virtual functions, where with normal virtual functions, you would need to have a definition of the base implementation for the function.

From here we are able to implement `IDamagable` into any class we feel needs to have a damage behaviour:

```cpp
class IDamagable
{
public:
	//virtual functions that are assigned a value of 0 are pure
	virtual int ApplyDamage(int dmg) = 0;
	
	virtual ~IDamagable() //deconstructor 
}

class Player: public IDamagable
{
protected:
	int health;
	int armour;

public:
	

	int ApplyDamage(int dmg) override
	{
		health -= (dmg / armour);	
	};
}

class Enemy: public IDamagable
{
protected:
	int health;

public:
	

	int ApplyDamage(int dmg) override
	{
		health -= dmg;	
	};
}

```

Note that when inheriting `IDamagable` to another class, we **MUST** prefix the inheritance definition with `public` allowing proper use of their overridden function behaviours
## Application of interfaces 

this allows use to customize the behaviour for many different classes but still pertain a clean execution with abstraction:

```cpp
int main()
{
	Bullet bull {};
	
	if(bull.colisionObj == IDamageable)
	{
		//valid for both player and enemy but will execute the abstracted behaviours!
		(IDamagable)bull.colisionObj.ApplyDamage(bull.dmg);
	}
}
```


we can also parse `IDamagable` within function calls but it **MUST** be a reference to the object and cannot be a copy otherwise it will execute the default virtual function definition in `IDamagable` and not the custom abstracted function defined in its inherited classes:

```cpp
class Bullet
{
protected:
	int damage = 12;

public:
	//getting a ref of the object we want to damage so it'll execute the proper abstracted function 
	DamageObject(IDamagable& obj)
	{
		obj.ApplyDamage(damage)
	}
}
```

