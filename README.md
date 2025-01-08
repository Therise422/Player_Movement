# Player_Movement

The first step is to open unity hub.
and make a project. you will need to name the project any name of your choice.
But for this tutorial i will call the project player movement.

When you open unity you will need to go to the scene 
button.


<img width="140" alt="image" src="https://github.com/user-attachments/assets/e69fa9e4-30e5-4f66-ac00-8560c584dad0" />



As seen in the picture I am on the scene button.
The next step is to make a platform for the player to walk on.

To make this you will go on the hierarchy, you right click on the hierarchy and you will go to 2d objects and spirte you can use squre, for platforms.

![image](https://github.com/user-attachments/assets/35a33897-6631-47b2-96f5-f08c16985cdd)

a bit of player movement while jumping 


![image](https://github.com/user-attachments/assets/56afb6bc-b110-4250-a91d-eadae772264a)




Then you will need to add a box collider to the squre,



![image](https://github.com/user-attachments/assets/c961f668-f156-46d1-baaf-93f44997b1dd)




that the player will walk on, however you will need to make the platoform with a squre you will need to make the squre to a rectangle.
I made one platform and you will just copy it and paste it again change the name to platform 2.
The total number of platforms is 2, for the level.


to make the player
then you go click on the hierarchy and you will go to 2d objects and spirte you can use triangle

The triangle will be the player.

you then need to make a scrpit for the player movement and call it player movement. and you drage the scrpit to add componet.

![image](https://github.com/user-attachments/assets/8136e5ea-f24e-4df1-8d60-94abdc1d82c4)


make sure you on the player object and add the scrpit to the player.
and make a game obeject and add the componment.
using UnityEngine;

public class PlayerMovement : MonoBehaviour
{
    private float horizontal;
    private float speed = 8f;
    private float jumpingPower = 16f;
    private bool isFacingRight = true;

    [SerializeField] private Rigidbody2D rb;
    [SerializeField] private Transform groundCheck;
    [SerializeField] private LayerMask groundLayer;

    void Update()
    {
        horizontal = Input.GetAxisRaw("Horizontal");

        if (Input.GetButtonDown("Jump") && IsGrounded())
        {
            rb.velocity = new Vector2(rb.velocity.x, jumpingPower);
        }

        if (Input.GetButtonUp("Jump") && rb.velocity.y > 0f)
        {
            rb.velocity = new Vector2(rb.velocity.x, rb.velocity.y * 0.5f);
        }

        Flip();
    }

    private void FixedUpdate()
    {
        rb.velocity = new Vector2(horizontal * speed, rb.velocity.y);
    }

    private bool IsGrounded()
    {
        return Physics2D.OverlapCircle(groundCheck.position, 0.2f, groundLayer);
    }

    private void Flip()
    {
        if (isFacingRight && horizontal < 0f || !isFacingRight && horizontal > 0f)
        {
            isFacingRight = !isFacingRight;
            Vector3 localScale = transform.localScale;
            localScale.x *= -1f;
            transform.localScale = localScale;
        }
    }
}

the horizontal part of the code is for player movement.
this is speed for player speed you make a private float speed = 8f;
which decides the speed of the player
 private float jumpingPower = 16f;bt this decides how mucj jumping force the player has.
 

This is the code i used for player movemnet and jumping.

create an empty game object. you put it at the button of your player 
craete a layer you call it isonground and assing floor is on ground.
you drag the rigidbody into the rigidbody in the script.
and drag the empty game object into player trasfourm in the scrpt.
you make the empty into the child of the player

you do this before the code.








