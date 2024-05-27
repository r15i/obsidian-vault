# Human eye 
![[Pasted image 20240113114029.png]]
- **Cornea**: external lens
- **Crystalline** lens : focus control [[Field of View and Focal Distance|focus]]
- **Iris** : thin, circular structure , responsible for controlling the diameter and size of the pupil  ([[Aperture]])
- **Pupil**: Hole located in the center of the iris that allows light to strike the retina 
- **Photo receptors neurons**:
     made of :
     - rods :  works with low sensitivity but with **colors**
     - cones: works with high sensitivity (on low light conditions) but with **greyscale** vision 

# Color Perception 
![[Pasted image 20240113114128.png]]
1. Cones transform the light in 3 signals based on 3 wavelenghts (red,green and blue) (**Trichromatism**)
2. Differential coding in terms on differences r/g, y/b and white/black done by specialized cells (**Color opponent process**)
![[Pasted image 20240113112335.png]]
### Trichromacy
Is the fenom by wich the color vision is due to the presence of 3 types of cones in the retina, and each one acts inside a specific bandwidth of light as a **low band-pass filters** in the bands of the visible range (r,g,b).

The cones measure this integral:
$$\hat{a}_{i} = \int_{350}^{780} C(\lambda) S_i(\lambda) \, d\lambda \,\,with\,\,\, i = r,g,b$$ 
where:
- $C(\lambda)$ : Spectral density of the light
- $S_i(\lambda)$ : response of each cones 
- $\hat{a}_{r},\hat{a}_{g},\hat{a}_{b}$ are the triplets representing the effects of the cones on each cone  
##### Metamerism
Colors with different spectral density can lead to the same set of $\hat{a}_{r},\hat{a}_{g},\hat{a}_{b}$ 
$\hat{a}_{i} = \int_{350}^{780} C_1(\lambda) S_i(\lambda) \, d\lambda =  \int_{350}^{780} C_2(\lambda) S_i(\lambda) \, d\lambda$ 


## Additive Color Synthesis
Each color can be represented with 3 values : 
### Chromatic coordinates
$$a_1P_1(\lambda) +a_2P_2(\lambda) +a_3P_3(\lambda) \iff C(\lambda)$$
$$a_rR(\lambda) +a_gG(\lambda) +a_bB(\lambda) \iff C(\lambda)$$
$$C(\lambda)\iff \sum^{3}_{i=1} \alpha_i\,P_i(\lambda) \implies a = \sum^{3}_{i=1} \alpha_i\,p_i$$
Not all triplets of coordinates correspond to physically realizable colors 
##### Negative coordinates
**Negative coordinates** correspond coloring that can not be obtained with the set of primaries.
- **Gamma** (gamut) of the color space is the set of colors physically realizable with **non-negative** primary colors in that space
### Chromaticity Coordinates
- 2 dimension (given $r+g+b =1$ )
- $r = \frac{R}{R+G+B}$, $g = \frac{G}{R+G+B}$, $b = \frac{B}{R+G+B}$
 - Convexity is preserved
##### Horseshoe diagram:
Intersection of the spectral colors curve with the plane 
$R+G+B =1$
- used for the **McAdam Ellipses**
	![[Pasted image 20240113130019.png]]
	
# Uniform Color Spaces 
Try to make ellipses more uniform 
![[Pasted image 20240113130141.png]]

## Additive and Subtractive Synthesis
![[Pasted image 20240113114255.png]]
Yellow, magenta and cyan can be obtained by a sum of the primaries (**additive** Synthesis) or by subtraction from the withe (**Subtractive** Synthesis)

# Color Matching Functions (CMF)
The "Color Matching Functions" (CMF) are a triplets of functions of the wavelength representing the chromatic coordinates $a(\lambda_i)$ of the spectral colors $E_i(\lambda)$ with respect to the primary of the typical observer of the [[Color Vision#CIE RGB 1931 Color Space|CIE RGB 1931 Color Space]] 


Allows to compute analytically the coordinates of a color $C(\lambda)$ drom the light spectrum (the reverse is impossible )

$r(\lambda)$ has negative values in thruth 
![[Pasted image 20240113121618.png]]


## Computation of Color Coordinates
1. **Spectral colors**: $$E_i(\lambda) = \delta(\lambda-\lambda_i)\approx rect(\frac{\lambda-\lambda_i}{\Delta\lambda})$$
   $\lambda_i$ rappresents the istance of light of the wave length,
   $\lambda$ rappresents the colors 
1.  Use spectral colors as primaries:
   $$C(\lambda) = \int_{350}^{780} C(\lambda') \delta(\lambda-\lambda') \, d\lambda' = \sum_i C(\lambda_i)E_i(\lambda)$$
3. Consider tristimulus values corresponding to spectral colors 
   $$ E_i(\lambda)\iff \alpha_1(\lambda_i) P_1(\lambda)+\alpha_2(\lambda_i) P_2(\lambda)+\alpha_3(\lambda_i) P_3(\lambda) $$
   note : $\alpha_i(\lambda)$ computes the single component by the wavelength  of the CMF
   
4. Compute to obtain $\beta_i$ (coordinates)
   note 
   $C(\lambda) = \sum_i C(\lambda_i)E_i(\lambda)$
	   $\downarrow$ use 3 
	   $= \sum_i C(\lambda_i)[\alpha_1 P_1(\lambda)+\alpha_2 P_2(\lambda)+\alpha_3 P_3(\lambda)]$ 
	   $\downarrow$ isolate $[\sum_i C(\lambda_i)\alpha_1] P_i(\lambda)$ for **each component**
	   $= [\sum_i C(\lambda_i)\alpha_1] P_1(\lambda)+[\sum_i C(\lambda_i)\alpha_2] P_2(\lambda)+[\sum_i C(\lambda_i)\alpha_3] P_3(\lambda)$
	   $=\beta_1 P_1(\lambda)+\beta_2 P_2(\lambda)+\beta_3 P_3(\lambda)$

So we can compute also as 	$$\beta_k = \int_{350}^{780} C(\lambda) \alpha_k(\lambda) \, d\lambda = \sum_i C(\lambda_i)\alpha_k(\lambda_i)$$
For each components end up as:
$R = \int_{350}^{780} C(\lambda) \hat{r}(\lambda) \, d\lambda \approx \sum_i C(\lambda_i)\hat{r}(\lambda_i)$
$G = \int_{350}^{780} C(\lambda) \hat{g}(\lambda) \, d\lambda \approx \sum_i C(\lambda_i)\hat{g}(\lambda_i)$
$B = \int_{350}^{780} C(\lambda) \hat{b}(\lambda) \, d\lambda \approx \sum_i C(\lambda_i)\hat{b}(\lambda_i)$

# Color Spaces
![[Pasted image 20240113120548.png]]

### CIE RGB 1931 Color Space
![[Pasted image 20240113124916.png]]
- Monogromatic primaries (Dirac delta functions)
- $C(\lambda) = R\cdot R(\lambda)+G\cdot G(\lambda)+B\cdot B(\lambda)$ 
### XYZ Color space
- obtained from RGB with linear tranformation 
![[Pasted image 20240113125050.png]]
- CMF POSITIVE
- $\hat{y}(\lambda)$ corresponds to the photopic response of the standared observer (luminous flux) 
##### Horseshoe diagram:
	![[Pasted image 20240113125700.png]]
- Intersection of the spectral colors curve with planes :
	$R+G+B=1$ or $X+Y+Z=1$

### CIELUV Color Space
![[Pasted image 20240113131837.png]]
### CIELAB Color Space
![[Pasted image 20240113131853.png]]

### sRGB Color Space 
![[Pasted image 20240113131916.png]]














