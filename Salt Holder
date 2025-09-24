import cadquery as cq

# Dimensions
height = 7.28    # inches
width = 4.33     # inches
depth = 2.76     # inches
thickness = 0.125  # material thickness in inches
hole_diameter = 0.25  # fastening hole

# Back plate
back = cq.Workplane("XY").rect(width, height).extrude(thickness)

# Side walls
side_panel = cq.Workplane("XY").rect(depth, height).extrude(thickness)

sides = (
    side_panel.translate((width/2 - thickness/2, depth/2, 0))
    .union(side_panel.translate((-width/2 + thickness/2, depth/2, 0)))
)

# Bottom plate
bottom = cq.Workplane("XY").rect(width, depth).extrude(thickness)
bottom = bottom.translate((0, depth/2, -thickness/2))

# Combine everything
holder = back.union(sides).union(bottom)

# Add a centered mounting hole on the back plate
holder = holder.faces(">Z").workplane(centerOption="CenterOfBoundBox").hole(hole_diameter)

# Export STEP file
cq.exporters.export(holder, "salt_lick_holder.step")

print("STEP file exported as salt_lick_holder.step")
