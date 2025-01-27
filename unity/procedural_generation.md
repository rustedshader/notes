# Procedural Generation

Set of rules and algorithms to automattically generate data.

# Procedural Generation vs Random Generation

We have set of rules on that basis we can generate data on in procedural generation.
To generate something meaningful.

# Procedural Generation in Unity 

## Seed

A Number that provides starting value or point for procedural generation 

## Basis

We can use DrawMeshInstance to create mesh according to random parameters to get a result.

- Bowyer Watson Algorithm
- Prim's Algorithm
- A* Algorithm
- Minimum Spanning Tree

## Hibert Curve

It is a continious fractol space filling curve


Here is how you will write its algorithm


procedure hilbert(x,y,xi,xj,yi,yj,n)

if (n<= 0) then
    LineTo( x + (xi + yi)/2, y + (xj + yj)/2 )
else
{
    hilbert(x,y,yi/2 , yj/2 ,xi / 2 , xj/2 , n-1);
    hilbert(x+xi/2,      y+xj/2 ,     xi/2, xj/2,  yi/2,  yj/2, n-1);
    hilbert(x+xi/2+yi/2, y+xj/2+yj/2, xi/2, xj/2,  yi/2,  yj/2, n-1);
    hilbert(x+xi/2+yi,   y+xj/2+yj,  -yi/2,-yj/2, -xi/2, -xj/2, n-1);
}

it is a recursive algorithm


void generateMap(){
    generatedMap = new int[width,height]
    for (int x = 1 ; x < width - 1 ; x++ ){
        for (int y = 1 ;  y < height -1 ; y++ ){
            generatedMap[x,y] = (pseudoRandom.Next(0,100) < fillingPercentage) ? 1 : 0 ;
        } 
    }
}

## To Create procedurally generated scenes we would 