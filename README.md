# Minecraft
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>3D Voxel Craft & Combat</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; user-select: none; }
        body, html { width: 100%; height: 100%; overflow: hidden; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background: #000; }
        #canvas-container { width: 100%; height: 100%; display: block; }
        
        /* UI Overlay */
        #ui-layer { position: absolute; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none; }
        
        /* Crosshair */
        #crosshair {
            position: absolute; top: 50%; left: 50%;
            width: 14px; height: 14px;
            transform: translate(-50%, -50%);
            pointer-events: none;
        }
        #crosshair::before, #crosshair::after {
            content: ''; position: absolute; background: rgba(255, 255, 255, 0.8);
            box-shadow: 0 0 2px rgba(0,0,0,0.8);
        }
        #crosshair::before { top: 6px; left: 0; width: 14px; height: 2px; }
        #crosshair::after { top: 0; left: 6px; width: 2px; height: 14px; }

        /* HUD Header */
        #hud-top {
            position: absolute; top: 15px; left: 15px;
            color: #fff; text-shadow: 2px 2px 4px rgba(0,0,0,0.8);
            font-size: 14px; font-weight: bold;
        }
        .stat-bar {
            width: 200px; height: 16px; background: rgba(0,0,0,0.6);
            border: 2px solid #555; border-radius: 4px; margin-top: 4px; overflow: hidden;
        }
        #hp-fill { width: 100%; height: 100%; background: #e74c3c; transition: width 0.2s; }

        /* Instructions Banner */
        #instructions {
            position: absolute; top: 50%; left: 50%;
            transform: translate(-50%, -50%);
            background: rgba(0, 0, 0, 0.85);
            border: 2px solid #555; border-radius: 8px;
            color:
