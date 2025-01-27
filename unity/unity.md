# Unity Notes


# What is Rigidbody? 

A Rigidbody in Unity is a fundamental component of the physics system that allows GameObjects to be affected by physical forces and interact realistically with other objects in the game world. Here are the key aspects of Rigidbodies in Unity:

# Adding W A S D to the rigibody 2d character

example

```c#
 public Rigidbody2D rb;
    private readonly float _speed = 0.5f;
    private readonly float _jumpSpeed = 7;
    
    void Start()
    {
        rb = GetComponent<Rigidbody2D>();
    }

    void Update()
    {
        if (Input.GetKeyDown(KeyCode.Space))
        {
          rb.AddForce(Vector2.up * _jumpSpeed, ForceMode2D.Impulse); 
        }
        if (Input.GetKey(KeyCode.D))
        {
            rb.AddForce(Vector2.right * _speed, ForceMode2D.Force); 
        }

        if (Input.GetKey(KeyCode.A))
        {
            rb.AddForce(Vector2.left * _speed, ForceMode2D.Force);
        }

    }
```

## Adding Jump to the rigidbody 2d Character

- First create a public rigidbody2d

```c#
 public Rigidbody2D rb;
 ```

- Then use this code to apply it 
```c#
rb = GetComponent<Rigidbody2D>().AddForce(jumpHeight, ForceMode2D.Impulse);
```

where jumpHeight is a Vector2;

```c# 
public Vector2 jumpHeight
```

# Transforming Camera W.R.T the character

- Create a Transform target
- Update the current Position wrt transform of the GameObject

- Why used -10f in z? 

    because the camera z axis is -10 in 2D Games


```c#
    public Transform target;
    
    void Update()
    {
        Vector3 newPost = new Vector3(target.position.x, target.position.y , -10f);
        transform.position = newPost;
    }
```


## * Note; KeyDown and Keyup for one input not continious input

# Collision in 2D Unity

```c#
private void OnCollisionEnter2D(Collision collision)
    {
        if (collision.gameObject.name == "box"){
            Debug.Log("Enter")
        }

        // Or Use Tags instead of gameObject Name

        if (collision.gameObject.CompareTag("obstacle")){
            Debug.Log("Enter the obstacle")
        }
    }

private void OnCollisionStay2D(Collision collision)
    {
        if (collision.gameObject.name == "box"){
            Debug.Log("Stay")
        }
    }

private void OnCollisionExit2D(Collision2D collision)
    {
        if (collision.gameObject.name == "box"){
            Debug.Log("Exit")
        }
    }
```

# Damage Dealing 2D Unity




# Hashsets

Just like sets but on sterioids

enum ArmorType {
    metalKneePlates,
    LeatherJacket,
    BikeHelmet
}

public class Character: Monobehaviour {
    private HashSet<ArmorType> equippedArmor = new HashSet<ArmorType>{
        ArmorType.LeatherJacket,
    };

    public void Equip(ArmorType armorType){
        equippedArmor.Add(armorType);
    }
}

# Random Walk Algorithms

https://www.noveltech.dev/procgen-random-walk


## Spawning New Objects



## Camera will move with player

## 