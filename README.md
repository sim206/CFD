<h1>Investigation of Mixed Natural-Forced Convection in Chimney Configurations</h1>


<h2>Description</h2>

This project aims to study the phenomenon of mixed natural-forced convection in chimney configurations found in various artificial environments. By analyzing the flow patterns, temperature distribution, and heat transfer rates within a specific geometry consisting of a heat chamber and a chimney, computational fluid dynamics (CFD) techniques will be used to understand the system's behaviour. The project aims to optimize the efficiency and minimize the environmental impact of chimney configurations used for waste disposal, energy production, and heat exchange applications. The findings will contribute to developing more efficient and sustainable chimney designs, supporting waste management and environmental conservation efforts.
<br />


<h2>Languages and Utilities Used</h2>

- <b>SolidWorks</b> 
- <b>ANSYS Workbench</b>
- <b>Matlab</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2>Project walk-through:</h2>

**1. Basic Mesh**

The geometry for the Heat-Chamber-Chimney system was created in ANSYS Fluent DesignModeler with dimensions in mm. It was then imported into ANSYS Mechanical, and a coarse mesh was generated. To improve mesh quality, edge divisions and biases were applied, along with a face mesh using quadrilateral cells. The refined mesh had increased element distribution at the heating chamber and channels, totalling 12,550 elements and 12,651 nodes. Further refinement may be necessary to address harsh transitions between parts. (Figure 1 shows the coarse mesh, and Figure 2 illustrates the refined mesh.)


<p align="center">
<img src="https://i.imgur.com/Nfq2xRU.png" height="80%" width="80%" alt="Heat chamber"/>
<br/>
</p>

**2. Basic Simulation**

The simulation, conducted with a Richardson number of 7.5 and an inlet velocity of 0.0578 m/s, revealed vortices at the outlet edges of the Heat-Chamber-Chimney System (HCCS). This occurrence was attributed to an insufficient mesh resolution, as the eddies could not be adequately captured. Figure 4 illustrates the velocity difference between the walls and the centre of the heat chamber, where fluid velocity increases as the HCCS width decreases from the inlet to the chamber. Consequently, the temperature distribution within the chamber exhibits higher temperatures near the walls and lower temperatures in the middle, as shown in figure 3.

<p align="center">
<img src="https://i.imgur.com/ignHXI0.png" height="80%" width="80%" alt="Heat chamber"/>
<br/>
</p>

**3.Critical Analysis of the Used Approach**

The Boussinesq approximation simulates buoyancy and natural convection by considering the density of the fluid to be dependent on temperature in the momentum equation while assuming constant density in the balance equations. The buoyancy force equation incorporates the production term, which accounts for density changes with temperature. This approximation reduces non-linearity but introduces slight errors. Two solver categories, pressure-based and density-based, are used based on flow conditions. Pressure solvers are suitable for incompressible low-speed flows, allowing for uncoupling of the balance equations and computational efficiency. Density-based solvers are used for high-speed fully compressible flows but require solving the coupled equations and are more computationally demanding. For Mach numbers below 0.3 indicating incompressible flow, a pressure-based solver can be utilized.

**4. Mesh Refinement Study**

A mesh refinement study was conducted as a course mesh cannot capture eddies sufficiently and a denser mesh would be needed, therefore decreasing the accuracy of the simulation. The number of elements was increased by approximately 15000 at each step for each mesh iteration.

<p align="center">
<img src="https://i.imgur.com/6ZheHpg.png"="80%" width="80%" alt="Heat chamber"/>
<br/>
</p>

Mesh refinement was performed by increasing the edge divisions by 10 at each step until convergence was achieved at Mesh 4. Plateauing maximum velocities and heat flux indicated convergence. To further refine the mesh, bias growth rates were increased at the heat chamber area to ensure smooth transitions and accurate cell discretization. Uniform grid structures were maintained for better convergence. Iterations were increased to ensure convergence at a steady state.

<p align="center">
<img src="https://i.imgur.com/VVKJDm9.png"="80%" width="80%" alt="Heat chamber"/>
<br/>
</p>

Figure 4 shows the refined Mesh 4, while Figure 5 indicates the convergence point of the heat flux in the simulation. The element density in the mesh effectively captures the simulation cells in areas of interest. The steady-state convergence was achieved at 3500 iterations. Skewness measurements confirmed acceptable element quality and orthogonal quality remained consistent at a value of 1 for each mesh refinement.

**5.Parametric Investigation**

In the first simulation, the width of the chamber was reduced from 10mm to 7mm. The velocity in the heat chamber increased significantly from 0.28m/s to 0.42m/s, as shown in Figure 8. This velocity change can be directly attributed to the 3mm decrease in the chamber width. The streamlines in the figure illustrate this effect. Additionally, the increased velocity has pushed the high temperature into the corners of the chimney, as the lighter hot fluid rises in the chimney region. The width of the chamber has a notable impact on the velocity and temperature of the system, which can be linked to the conservation of mass formula.

<p align="center">
<img src="https://i.imgur.com/30x5Bhl.png"="80%" width="80%" alt="Heat chamber"/>
<br/>
</p>

<p align="center">
<img src="https://i.imgur.com/3NVW3qf.png"="80%" width="80%" alt="Heat chamber"/>
<br/>
</p>

In the second simulation, decreasing the width of the chimney from 22mm to 20mm had minimal impact on the heat flux and maximum velocities, as observed in Figure 9 and Table 2, suggesting that the chimney width has a negligible effect on the model.

<p align="center">
<img src="https://i.imgur.com/2KRE3mB.png"="80%" width="80%" alt="Heat chamber"/>
<br/>
</p>

The Ri numbers were chosen between 5 and 8 and compared to Ri=7.5 to investigate the relationship between the inlet velocity and the maximum velocities and heat flux.

<p align="center">
<img src="https://i.imgur.com/pByn1tZ.png"="80%" width="80%" alt="Heat chamber"/>
<br/>
</p>

it can be noted that the velocity in the x and y direction decrease as the inlet velocity decreases and the Richardson number increases. This is expected as high velocities increase the temperature which is verified as heat flux remains high at a low Ri number.

<p align="center">
<img src="https://i.imgur.com/VSt5gXG.png"="80%" width="80%" alt="Heat chamber"/>
<br/>
</p>

<p align="center">
<img src="https://i.imgur.com/E7H3OGX.png"="80%" width="80%" alt="Heat chamber"/>
<br/>
</p>

**6. Identification of a relevant turbulence model**

RANS (Reynolds-averaged Navier-Stokes) and LES (Large Eddy Simulation) are turbulence models used in commercial software. RANS models the average behavior of turbulent flow over time, capturing stresses without requiring an iteration time step. It is computationally intensive, solving balance equations and two partial differential equations. LES confirms thermal convection by capturing additional mixing from buoyancy, automatically considering small-scale eddies with a sub-grid velocity. For high Rayleigh numbers, LES is more suitable, and increasing mesh density improves its ability to capture and store solutions faster due to the uniform nature of the geometry.

